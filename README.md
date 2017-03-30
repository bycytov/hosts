# hosts
hosts file from internet. Combined sources for mobile and desktop.


################INSTALLATION

Open the hosts text file in Notepad, TextEdit, or Notepad++, or another text editor. Highlight all the text in the file and copy it.
1. Go to your router's web interface through your web browser, typically by entering the URL http://192.168.1.1. If you assigned your router a different local IP address, use that instead.
2. In the web interface, click on the Services tab. Enter your DD-WRT router username and password, if prompted.
3. Scroll down to the 'DNSMasq' section. Make sure that DNSMasq bullet and Local DNS bullets are set to 'Enable' that no other DNSMasq options are set.
4. Use Putty or another Telnet client to connect to the router's Telnet interface. (That is, connect to the router's local IP address on port 23 - telnet.)
5. Enter your login and password. The password will be the same as for the web interface. For the username, first try root. If that does not work, try the same username as for the web interface.
6. At the DD-WRT command prompt, type killall DNSMasq and hit enter.
7. Type pwd and hit enter. You should get back "/tmp/root". Type cd .. and hit enter.
8. At the next prompt, type cat > hosts and hit enter.
9. Paste all the text you copied earlier from the hosts.txt file. (For example, in Putty, bring your mouse cursor to the cursor location at the bottom of the telnet window and click your right mouse button to paste.)
10. After a minute or so of the text pasting/transferring, the screen will stop scrolling. When that happens, finish the file with a Ctrl-D key combination.
11. Type dnsmasq --conf-file=/tmp/dnsmasq.conf --addn-hosts=/tmp/hosts and hit enter.
12. You are now finished. Type exit and hit enter.
13. Test out your configuration. Use a computer or connected device to use the local commands "ping" or "tracert" on known good sites (like google.com) vs. sites on the hosts list. The known good sites should have much higher ping times than the sites on the hosts list (for example, 12 ms versus less than 1 ms). The "tracert" (traceroute) comamnd should show a much lengthier Internet path to the good site than the bad site (which should only be one or two hops).
14. Again, repeat all these steps if your router goes down or is rebooted for some reason.
