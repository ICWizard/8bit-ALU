module alu_8bit(
    input  [7:0] a,
    input  [7:0] b,
    input  [2:0] op,
    output reg [7:0] result,
    output zero,
    output carry,
    output overflow
);

reg c_out;

always @(*) begin
    case(op)
        3'b000: {c_out, result} = a + b;     // ADD
        3'b001: {c_out, result} = a - b;     // SUB
        3'b010: result = a & b;              // AND
        3'b011: result = a | b;              // OR
        3'b100: result = a ^ b;              // XOR
        default: result = 8'b0;
    endcase
end

assign carry = c_out;
assign zero = (result == 8'b0);
assign overflow = (op == 3'b000) ? 
                  ((a[7] & b[7] & ~result[7]) | (~a[7] & ~b[7] & result[7])) :
                  1'b0;

endmodule
