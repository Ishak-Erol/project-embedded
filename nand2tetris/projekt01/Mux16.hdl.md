// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/1/Mux16.hdl
/**
 * 16-bit multiplexor: 
 * for i = 0, ..., 15:
 * if (sel = 0) out[i] = a[i], else out[i] = b[i]
 */
CHIP Mux16 {
    IN a[16], b[16], sel;
    OUT out[16];

    PARTS:
    Not(in=sel, out=notsel);

    And(a=a[0], b=notsel, out=aAndnotsel0);
    And(a=sel, b=b[0], out=selAndb0);
    Or(a=aAndnotsel0, b=selAndb0, out=out[0]);

    And(a=a[1], b=notsel, out=aAndnotsel1);
    And(a=sel, b=b[1], out=selAndb1);
    Or(a=aAndnotsel1, b=selAndb1, out=out[1]);

    And(a=a[2], b=notsel, out=aAndnotsel2);
    And(a=sel, b=b[2], out=selAndb2);
    Or(a=aAndnotsel2, b=selAndb2, out=out[2]);

    And(a=a[3], b=notsel, out=aAndnotsel3);
    And(a=sel, b=b[3], out=selAndb3);
    Or(a=aAndnotsel3, b=selAndb3, out=out[3]);

    And(a=a[4], b=notsel, out=aAndnotsel4);
    And(a=sel, b=b[4], out=selAndb4);
    Or(a=aAndnotsel4, b=selAndb4, out=out[4]);

    And(a=a[5], b=notsel, out=aAndnotsel5);
    And(a=sel, b=b[5], out=selAndb5);
    Or(a=aAndnotsel5, b=selAndb5, out=out[5]);

    And(a=a[6], b=notsel, out=aAndnotsel6);
    And(a=sel, b=b[6], out=selAndb6);
    Or(a=aAndnotsel6, b=selAndb6, out=out[6]);

    And(a=a[7], b=notsel, out=aAndnotsel7);
    And(a=sel, b=b[7], out=selAndb7);
    Or(a=aAndnotsel7, b=selAndb7, out=out[7]);

    And(a=a[8], b=notsel, out=aAndnotsel8);
    And(a=sel, b=b[8], out=selAndb8);
    Or(a=aAndnotsel8, b=selAndb8, out=out[8]);

    And(a=a[9], b=notsel, out=aAndnotsel9);
    And(a=sel, b=b[9], out=selAndb9);
    Or(a=aAndnotsel9, b=selAndb9, out=out[9]);

    And(a=a[10], b=notsel, out=aAndnotsel10);
    And(a=sel, b=b[10], out=selAndb10);
    Or(a=aAndnotsel10, b=selAndb10, out=out[10]);

    And(a=a[11], b=notsel, out=aAndnotsel11);
    And(a=sel, b=b[11], out=selAndb11);
    Or(a=aAndnotsel11, b=selAndb11, out=out[11]);

    And(a=a[12], b=notsel, out=aAndnotsel12);
    And(a=sel, b=b[12], out=selAndb12);
    Or(a=aAndnotsel12, b=selAndb12, out=out[12]);

    And(a=a[13], b=notsel, out=aAndnotsel13);
    And(a=sel, b=b[13], out=selAndb13);
    Or(a=aAndnotsel13, b=selAndb13, out=out[13]);

    And(a=a[14], b=notsel, out=aAndnotsel14);
    And(a=sel, b=b[14], out=selAndb14);
    Or(a=aAndnotsel14, b=selAndb14, out=out[14]);

    And(a=a[15], b=notsel, out=aAndnotsel15);
    And(a=sel, b=b[15], out=selAndb15);
    Or(a=aAndnotsel15, b=selAndb15, out=out[15]);}