// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/1/And16.hdl
/**
 * 16-bit And gate:
 * for i = 0, ..., 15:
 * out[i] = a[i] And b[i] 
 */
CHIP And16 {
    IN a[16], b[16];
    OUT out[16];

    PARTS:
Nand(a=a[0], b=b[0], out=anotAndb0);
    Not(in=anotAndb0, out=out[0]);

    Nand(a=a[1], b=b[1], out=anotAndb1);
    Not(in=anotAndb1, out=out[1]);

    Nand(a=a[2], b=b[2], out=anotAndb2);
    Not(in=anotAndb2, out=out[2]);

    Nand(a=a[3], b=b[3], out=anotAndb3);
    Not(in=anotAndb3, out=out[3]);

    Nand(a=a[4], b=b[4], out=anotAndb4);
    Not(in=anotAndb4, out=out[4]);

    Nand(a=a[5], b=b[5], out=anotAndb5);
    Not(in=anotAndb5, out=out[5]);

    Nand(a=a[6], b=b[6], out=anotAndb6);
    Not(in=anotAndb6, out=out[6]);

    Nand(a=a[7], b=b[7], out=anotAndb7);
    Not(in=anotAndb7, out=out[7]);

    Nand(a=a[8], b=b[8], out=anotAndb8);
    Not(in=anotAndb8, out=out[8]);

    Nand(a=a[9], b=b[9], out=anotAndb9);
    Not(in=anotAndb9, out=out[9]);

    Nand(a=a[10], b=b[10], out=anotAndb10);
    Not(in=anotAndb10, out=out[10]);

    Nand(a=a[11], b=b[11], out=anotAndb11);
    Not(in=anotAndb11, out=out[11]);

    Nand(a=a[12], b=b[12], out=anotAndb12);
    Not(in=anotAndb12, out=out[12]);

    Nand(a=a[13], b=b[13], out=anotAndb13);
    Not(in=anotAndb13, out=out[13]);

    Nand(a=a[14], b=b[14], out=anotAndb14);
    Not(in=anotAndb14, out=out[14]);

    Nand(a=a[15], b=b[15], out=anotAndb15);
    Not(in=anotAndb15, out=out[15]);}