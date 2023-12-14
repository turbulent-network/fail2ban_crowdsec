# crowdsec action for fail2ban

This basically consists of creating the `crowdsec.conf` file in `/etc/fail2ban/action.d` dir, then editing the files in `/etc/fail2ban/jail.d` to use the new action...

Idea comes from [https://discourse.crowdsec.net/t/fail2ban-as-agent-for-crowdsec/910/3](https://discourse.crowdsec.net/t/fail2ban-as-agent-for-crowdsec/910/3).


## Install

To "install" this setup, you'll need to clone the repo:

    git clone https://github.com/turbulent-network/fail2ban_crowdsec
    cd fail2ban_crowdsec

Then create symlinks to your fail2ban folder:

    sudo ln -vs $PWD/action.d/crowdsec.conf /etc/fail2ban/action.d/
    sudo ln -vs $PWD/jail.d/* /etc/fail2ban/jail.d/


## Uninstall

Uninstall using:

    for i in action.d/* jail.d/*; do
        [[ $i && -e $i && -e /etc/fail2ban/$i ]] && sudo rm -i /etc/fail2ban/$i
    done


