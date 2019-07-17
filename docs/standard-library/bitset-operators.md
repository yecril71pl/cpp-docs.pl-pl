---
title: '&lt;bitset —&gt; operatorów'
ms.date: 11/04/2016
f1_keywords:
- bitset/std::operator&amp;
- bitset/std::operator&gt;&gt;
- bitset/std::operator&lt;&lt;
- bitset/std::operator^
- bitset/std::operator|
ms.assetid: 84fe6a13-6f6e-4cdc-bf8f-6f65ab1134d4
helpviewer_keywords:
- std::operator&amp; (bitset)
- std::operator&gt;&gt; (bitset)
- std::operator&lt;&lt; (bitset)
ms.openlocfilehash: 30367e003d2dad95e870854098e7fcae34f50efa
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243333"
---
# <a name="ltbitsetgt-operators"></a>&lt;bitset —&gt; operatorów

## <a name="op_amp"></a> Operator&amp;

Wykonuje bitową operację `AND` między dwoma bitsets.

```cpp
template <size_t size>
bitset<size>
operator&(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Pierwsza z dwóch bitsets, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `AND`.

*po prawej stronie*\
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `AND`.

### <a name="return-value"></a>Wartość zwracana

Bitset —, której elementy są wynikiem wykonania `AND` operacji na odpowiadające elementy *po lewej stronie* i *prawo*.

### <a name="example"></a>Przykład

```cpp
// bitset_and.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 & b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0001
```

## <a name="op_lt_lt"></a> Operator&lt;&lt;

Wstawia tekstowa reprezentacja bitową sekwencję do strumienia wyjściowego.

```
template <class CharType, class Traits, size_t N>
basic_ostream<CharType, Traits>& operator<<(
    basic_ostream<CharType, Traits>& ostr,
    const bitset<N>& right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*\
Obiekt typu **bitset —\<N >** który ma zostać wstawiony do strumienia wyjściowego, jako ciąg.

### <a name="return-value"></a>Wartość zwracana

Tekstowa reprezentacja bitową sekwencję w `ostr`.

### <a name="remarks"></a>Uwagi

Przeciążenia funkcji szablonu `operator<<`, dzięki czemu zestawu bitów do zapisania bez uprzedniego przekonwertowania na ciąg. Funkcja szablonu skutecznie wykonuje:

**OSTR** << _*po prawej stronie*. [to_string —](bitset-class.md) <**CharType**, **cech**, **alokatora**\<**CharType**>>)

### <a name="example"></a>Przykład

```cpp
// bitset_op_insert.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 9 );

   // bitset inserted into output stream directly
   cout << "The ordered set of bits in the bitset<5> b1(9)"
        << "\n can be output with the overloaded << as: ( "
        << b1 << " )" << endl;

   // Compare converting bitset to a string before
   // inserting it into the output steam
   string s1;
   s1 =  b1.template to_string<char,
      char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

## <a name="op_gt_gt"></a> Operator&gt;&gt;

Odczytuje ciąg znaków bit do zestawu bitów.

```
template <class CharType, class Traits, size_t Bits>
basic_istream<CharType, Traits>& operator>> (
    basic_istream<CharType, Traits>&
_Istr,
    bitset<N>&
    right);
```

### <a name="parameters"></a>Parametry

*_Istr*\
Ciąg, który jest wprowadzany do strumienia wejściowego, który ma zostać wstawiony do bitset —.

*po prawej stronie*\
Bitset — otrzymuje bity ze strumienia wejściowego.

### <a name="return-value"></a>Wartość zwracana

Funkcja szablonu zwraca ciąg *_Istr*.

### <a name="remarks"></a>Uwagi

Przeciążenia funkcji szablonu `operator>>` do przechowywania w _ bitset — *po prawej stronie* bitset — wartość (`str`), gdzie `str` jest obiektem typu [basic_string](basic-string-class.md)  <  **CharType**, **cech**, **alokatora** \< **CharType**>> **&** wyodrębnione z *_Istr*.

Funkcja szablonu wyodrębnia elementy z *_Istr* i wstawia je do bitset — aż do:

- Wszystkie elementy bit zostały wyodrębnione ze strumienia wejściowego i przechowywane w bitset —.

- Bitset — jest wypełnione z użyciem usługi bits ze strumienia wejściowego.

- Napotkano element wejściowy nie jest 0 ani 1.

### <a name="example"></a>Przykład

```cpp
#include <bitset>
#include <iostream>
#include <string>

using namespace std;
int main()
{

   bitset<5> b1;
   cout << "Enter string of (0 or 1) bits for input into bitset<5>.\n"
        << "Try bit string of length less than or equal to 5,\n"
        << " (for example: 10110): ";
   cin >>  b1;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<5> b1 as: ( "
        << b1 << " )" << endl;

   // Truncation due to longer string of bits than length of bitset
   bitset<2> b3;
   cout << "Enter string of bits (0 or 1) for input into bitset<2>.\n"
        << " Try bit string of length greater than 2,\n"
        << " (for example: 1011): ";
   cin >>  b3;

   cout << "The ordered set of bits entered from the "
        << "keyboard\n has been input into bitset<2> b3 as: ( "
        << b3 << " )" << endl;

   // Flushing the input stream
   char buf[100];
   cin.getline(&buf[0], 99);

   // Truncation with non-bit value
   bitset<5> b2;
   cout << "Enter a string for input into  bitset<5>.\n"
        << " that contains a character than is NOT a 0 or a 1,\n "
        << " (for example: 10k01): ";
   cin >>  b2;

   cout << "The string entered from the keyboard\n"
        << " has been input into bitset<5> b2 as: ( "
        << b2 << " )" << endl;
}
```

## <a name="op_xor"></a> operator ^

Wykonuje bitową operację `EXCLUSIVE-OR` między dwoma bitsets.

```cpp
template <size_t size>
bitset<size>
operator^(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Pierwsza z dwóch bitsets, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `EXCLUSIVE-OR`.

*po prawej stronie*\
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `EXCLUSIVE-OR`.

### <a name="return-value"></a>Wartość zwracana

Bitset —, której elementy są wynikiem wykonania `EXCLUSIVE-OR` operacji na odpowiadające elementy *po lewej stronie* i *prawo*.

### <a name="example"></a>Przykład

```cpp
// bitset_xor.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 ^ b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0110
```

## <a name="op_or"></a> operator&#124;

Wykonuje bitową operację `OR` między dwoma bitsets.

```cpp
template <size_t size>
bitset<size>
operator|(
    const bitset<size>& left,
    const bitset<size>& right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*\
Pierwsza z dwóch bitsets, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `OR`.

*po prawej stronie*\
Drugi dwóch valarrays, w której odpowiednie elementy, które mają być łączone za pomocą operatora testu koniunkcji `OR`.

### <a name="return-value"></a>Wartość zwracana

Bitset —, której elementy są wynikiem wykonania `OR` operacji na odpowiadające elementy *po lewej stronie* i *prawo*.

### <a name="example"></a>Przykład

```cpp
// bitset_or.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

using namespace std;

int main()
{
   bitset<4> b1 ( string("0101") );
   bitset<4> b2 ( string("0011") );
   bitset<4> b3 = b1 | b2;
   cout << "bitset 1: " << b1 << endl;
   cout << "bitset 2: " << b2 << endl;
   cout << "bitset 3: " << b3 << endl;
}
```

```Output
bitset 1: 0101
bitset 2: 0011
bitset 3: 0111
```
