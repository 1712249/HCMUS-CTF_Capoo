## Decoder
- Chuỗi kết thúc ==, đây có thể là base64
- Base64 decode ra được:
- I think the flag is encoded in base(64/2): JBBU2VKTFVBVIRT3NJKXG5C7KNUW24DMIVPUIZLDN5SGK4T5
- Base32 decode ra được:
HCMUS-CTF{jUst_SimplE_Decoder}

## Factorization
- Parse file public.pem tìm được n và e
- Factor n tìm được p và q
- Giải ra m, viết hàm long_to_str để giải ra flag:
- ![alt text](https://github.com/1712249/HCMUS-CTF_Capoo/blob/master/aquawind0130/Factorization.bmp)
- HCMUS-CTF{smaLL_NumbeR}

## Smalle
- Parse file public.pem tìm được n và e 
- ![alt text](https://github.com/1712249/HCMUS-CTF_Capoo/blob/master/aquawind0130/Smalle.png)
- Do e nhỏ nên ta thử với từng x=0,1,2,.. sao cho m nguyên
- Chạy code thử với x=1 thì m nguyên
- Tìm được m, hexdump file xorkey ra được:
abaca4adb0c4bfaab18295849b8191b6849c9192b2959e86b59b828f998a39ee7ca4e1e25abc704452d5c6a6852c93335f043791b69d2306e06b312b
- Xor với m, tìm được:
HCMUS-CTF{hello_from_the_other_sidezzzzzzzzzzzzzzzzzzzzzzzz}
- Nộp thử, fail, bỏ đống z đi, flag:
HCMUS-CTF{hello_from_the_other_side}

## Factorization Revenge
- Ta có:
- ![alt text](https://github.com/1712249/HCMUS-CTF_Capoo/blob/master/aquawind0130/Factorization%20Revenge.png)
- Giải phương trình X^2-ddX-n=0, được 2 nghiệm là p và -q
- Từ p và q tìm được d, giải ra m
- Dùng hàm long_to_str để giải ra flag
- ![alt text](https://github.com/1712249/HCMUS-CTF_Capoo/blob/master/aquawind0130/Factorization%20Revenge.bmp) 
- HCMUS-CTF{haaaaah_what_do_you_really_want_from_meeeeeee}

## Very Secure RSA
- Dùng tool attack RSA https://github.com/Ganapati/RsaCtfTool, tìm được m
- Dùng hàm long_to_str để giải ra flag
 - ![alt text](https://github.com/1712249/HCMUS-CTF_Capoo/blob/master/aquawind0130/Very%20Secure%20RSA.bmp)
- HCMUS-CTF{c775e7b757ede630cd0aa1113bd102661ab38829ca52a6422ab782862f268646}
