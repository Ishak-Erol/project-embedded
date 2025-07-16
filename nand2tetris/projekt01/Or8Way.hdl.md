// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/1/Or8Way.hdl
/**
 * 8-way Or gate: 
 * out = in[0] Or in[1] Or ... Or in[7]
 */
CHIP Or8Way {
    IN in[8];
    OUT out;

    PARTS:
    Not(in=in[0], out=firnandlayer0);
    Not(in=in[1], out=firnandlayer1);
    Nand(a=firnandlayer0, b=firnandlayer1, out=notAnd01);

    Not(in=in[2], out=firnandlayer2);
    Not(in=in[3], out=firnandlayer3);
    Nand(a=firnandlayer2, b=firnandlayer3, out=notAnd23);

    Not(in=in[4], out=firnandlayer4);
    Not(in=in[5], out=firnandlayer5);
    Nand(a=firnandlayer4, b=firnandlayer5, out=notAnd45);

    Not(in=in[6], out=firnandlayer6);
    Not(in=in[7], out=firnandlayer7);
    Nand(a=firnandlayer6, b=firnandlayer7, out=notAnd67);

    Not(in=notAnd01 , out=secnandlayer01 );
    Not(in=notAnd23 , out=secnandlayer23 );
    Nand(a=secnandlayer01, b=secnandlayer23, out=notAnd0123);

    Not(in=notAnd45 , out= secnandlayer45);
    Not(in=notAnd67 , out=secnandlayer67 );
    Nand(a=secnandlayer45, b=secnandlayer67, out=notAnd4567);

    Not(in=notAnd0123 , out=thirdnandlayer0123 );
    Not(in=notAnd4567 , out=thirdnandlayer4567);
    Nand(a=thirdnandlayer0123, b=thirdnandlayer4567, out=out);

}