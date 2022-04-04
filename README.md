
// SPDX-License-Identifier: MIT
pragma solidity >=0.7.0 <0.9.0;

contract Calculator {
   uint result;
   uint account_balance = 0;
   uint sell_count = 0;
   uint current_price;
   uint sell_price;
   uint royalty_fraction = 0;
   uint[] data;
   uint[] passbook;
   uint[] inp1;
   uint[] inp2;
   uint[] out;

    function add(uint x, uint y) public {
        result = x + y;
        inp1.push(x);
        inp2.push(y);
        out.push(result);     

    }

    function sub(uint x, uint y) public {
        result = x - y;
    }

    function multiply(uint x, uint y) public {
        result = x * y;
    }

    function devide(uint x, uint y) public {
        require(y!=0, 'Division by zero not possible');
        result = x / y;
    }

    function get() public view returns (uint) {
        return result;

}
    function show_record() public view returns(uint[] memory, uint[] memory, uint[] memory){
        return (inp1, inp2, out);
        
    }
    
    function SELL(uint price) public {
        current_price = price*(1000000000);
        account_balance = account_balance + (royalty_fraction * current_price)/100;
        data.push(price);
        passbook.push(account_balance);
        
    }
    function MINT(uint mint_price, uint royalty) public{
        account_balance = account_balance + mint_price*(1000000000);
        royalty_fraction = royalty;
        data.push(mint_price);
        passbook.push(account_balance);
    }
    function check_balance() public view returns (uint) {
        return account_balance;
        
}
    
    function sell_history() public view returns(
      uint[] memory){  
        return (data);  
    }
    
    function passbook_viewer() public view returns(
      uint[] memory){  
        return (passbook);  
    }
    }
    