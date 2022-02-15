# simatic-s7-2xx
~~~text
int decodeS72xx(unsigned char* data, int len) {
    unsigned char c = 0xaa;
    unsigned char p0=0;
    unsigned char p1=0;
    for(int i=0; i<len; i++) {
        unsigned char x = data[i];
        if(i%2) {
            data[i]^=(p0^c);
            p0 = x;
        } else {
            data[i]^=(p1^c);
            p1 = x;
        }
    }
    return 0;
}
~~~
