# ksms

I've seen other stuff on github and they are bloat. Here is how you do it really nice and easy.

Dependencies:
+ kdeconnect (duh)
+ fzf or dmenu or rofi. I used fzf here
+ contacts file that looks like this `NAME +123456789`.

You will also need to run `kdeconnect-cli -l` to get the id that is going to be placed in the code bellow. This code is a function you can through in a script or in your .bashrc, .zshrc etc.

```
ksms() {
	number=`cat ~/Documents/contacts | fzf | cut -d '+' -f2 | tr -d '\n'`
	kdeconnect-cli --device "YOUR_ID_HERE" --send-sms "$@" --destination "$number"
}
```

Usage: `ksms "message"` then fzf will let you choose a number. And that's about it. Real simple, no building, no sudo no nothing.
