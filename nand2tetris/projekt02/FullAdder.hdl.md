// This file is part of www.nand2tetris.org
// and the book "The Elements of Computing Systems"
// by Nisan and Schocken, MIT Press.
// File name: projects/2/FullAdder.hdl
/**
 * Computes the sum of three bits.
 */
CHIP FullAdder {
    IN a, b, c;  // 1-bit inputs
    OUT sum,     // Right bit of a + b + c
        carry;   // Left bit of a + b + c

    PARTS:
    //Xor(a = a , b = b, out = aXorb);
    //Xor(a = aXorb, b = c, out = sum );
    //And(a= a, b= b, out= aAndb);
    //Mux(a= aAndb, b= c, sel= aXorb, out= carry);
    HalfAdder(a=a, b=b, sum=sum1, carry=carry1);
    HalfAdder(a=sum1, b=c, sum=sum, carry=carry2);
    Or(a=carry2, b=carry1, out=carry);
}