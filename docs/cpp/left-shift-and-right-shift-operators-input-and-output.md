---
title: Operatory przesunięcia w lewo i w prawo (&gt; &gt; i &lt; &lt;) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- <<
- '>>'
dev_langs:
- C++
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dece9ac4045fa8b46e5edf8b266312242000229
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Operatory przesunięcia w lewo i w prawo (&gt; &gt; i &lt; &lt;)
Operatory przesunięcia bitowego to operator przesunięcia w prawo (>>), który przenosi bity *wyrażenia przesunięcia* w prawo i operator przesunięcia w lewo (<<), który przenosi bity *shiftwyrażenie* po lewej stronie. <sup>1</sup>  
  
## <a name="syntax"></a>Składnia  
  
> *wyrażenie SHIFT* `<<` *wyrażenie dodatku*  
> *wyrażenie SHIFT* `>>` *wyrażenie dodatku*  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Następujące opisy i przykłady są prawidłowe w systemie Windows dla architektur x86 i x64. Implementacja operatorów przesunięcia w lewo i przesunięcia w prawo znacznie się różni w systemie Windows RT dla urządzeń ARM. Aby uzyskać więcej informacji, zobacz sekcję "Shift — operatory" [Hello ARM](http://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) wpis w blogu.  
  
## <a name="left-shifts"></a>Przesunięcia w lewo  
 Operator przesunięcia w lewo powoduje, że usługa bits w *wyrażenia przesunięcia* lekkie po lewej stronie przez liczbę pozycji określony przez *dodatku wyrażenia*. Pozycje bitów, które zostały zwolnione w wyniku operacji przesunięcia, są wypełniane przez zera. Przesunięcie w lewo to przesunięcie logiczne (bity, które zostaną przesunięte poza koniec, są odrzucane, łącznie z bitem znaku). Aby uzyskać więcej informacji o rodzajach bitowe zmian, zobacz [przesunięcia bitowego](http://en.wikipedia.org/wiki/Bitwise_shift).  
  
 W poniższym przykładzie pokazano operacje przesunięcia w lewo przy użyciu liczb bez znaku. W przykładzie pokazano, co się dzieje z bitami, poprzez reprezentowanie wartości jako zestawu bitów. Aby uzyskać więcej informacji, zobacz [bitset — klasa](../standard-library/bitset-class.md).  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short1 = 4;      
    bitset<16> bitset1{short1};   // the bitset representation of 4  
    cout << bitset1 << endl;  // 0000000000000100  
  
    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;  // 0000000000001000  
  
    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16  
    bitset<16> bitset3{short3};  
    cout << bitset3 << endl;  // 0000000000010000  
}  
  
```  
  
 Jeśli przesuniesz liczbę ze znakiem w lewo, tak że bit znaku zostanie objęty zmianą, wynik będzie nieokreślony. Poniższy przykład pokazuje, co się dzieje w Visual C++, gdy 1 bit jest przesunięty w lewo do pozycji bitu znaku.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 16384;      
    bitset<16> bitset1{short2};  
    cout << bitset1 << endl;  // 0100000000000000   
  
    short short3 = short1 << 1;  
    bitset<16> bitset3{short3};  // 16384 left-shifted by 1 = -32768  
    cout << bitset3 << endl;  // 100000000000000  
  
    short short4 = short1 << 14;  
    bitset<16> bitset4{short4};  // 4 left-shifted by 14 = 0  
    cout << bitset4 << endl;  // 000000000000000    
}  
```  
  
## <a name="right-shifts"></a>Przesunięcia w prawo  
 Operator przesunięcia w prawo powoduje wzorca bitowego w *wyrażenia przesunięcia* lekkie po prawej stronie przez liczbę pozycji określony przez *dodatku wyrażenia*. W przypadku liczb bez znaku, pozycje bitów, które zostały zwolnione w wyniku operacji przesunięcia, są wypełniane przez zera. W przypadku liczb ze znakiem, bit znaku jest używany do wypełniania opuszczonych pozycji bitów. Innymi słowy, jeśli liczba jest dodatnia, używane jest 0, a jeśli liczba jest ujemna, używane jest 1.  
  
> [!IMPORTANT]
> Wynik przesunięcia w prawo liczby ujemnej ze znakiem zależy od implementacji. Mimo że Visual C++ używa bitu znaku do wypełnienia zwolnionych pozycji bitów, nie ma gwarancji, że inne implementacje działają tak samo.  
  
 W tym przykładzie pokazano operacje przesunięcia w prawo przy użyciu liczb bez znaku:  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned short short11 = 1024;  
    bitset<16> bitset11{short11};  
    cout << bitset11 << endl;     // 0000010000000000  
  
    unsigned short short12 = short11 >> 1;  // 512  
    bitset<16> bitset12{short12};  
    cout << bitset12 << endl;     // 0000001000000000  
  
    unsigned short short13 = short11 >> 10;  // 1  
    bitset<16> bitset13{short13};  
    cout << bitset13 << endl;     // 0000000000000001  
  
    unsigned short short14 = short11 >> 11;  // 0  
    bitset<16> bitset14{short14};  
    cout << bitset14 << endl;     // 0000000000000000}  
}  
```  
  
 W kolejnym przykładzie pokazano operacje przesunięcia w prawo przy użyciu liczb dodatnich ze znakiem.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short short1 = 1024;  
    bitset<16> bitset1{short1};  
    cout << bitset1 << endl;     // 0000010000000000  
  
    short short2 = short1 >> 1;  // 512  
    bitset<16> bitset2{short2};  
    cout << bitset2 << endl;     // 0000001000000000  
  
    short short3 = short1 >> 11;  // 0  
    bitset<16> bitset3{short3};     
    cout << bitset3 << endl;     // 0000000000000000  
}  
```  
  
 W następnym przykładzie pokazano operacje przesunięcia w prawo przy użyciu ujemnych liczb całkowitych ze znakiem.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    short neg1 = -16;  
    bitset<16> bn1{neg1};  
    cout << bn1 << endl;  // 1111111111110000  
  
    short neg2 = neg1 >> 1; // -8  
    bitset<16> bn2{neg2};  
    cout << bn2 << endl;  // 1111111111111000  
  
    short neg3 = neg1 >> 2; // -4  
    bitset<16> bn3{neg3};  
    cout << bn3 << endl;  // 1111111111111100  
  
    short neg4 = neg1 >> 4; // -1  
    bitset<16> bn4{neg4};      
    cout << bn4 << endl;  // 1111111111111111  
  
    short neg5 = neg1 >> 5; // -1   
    bitset<16> bn5{neg5};      
    cout << bn5 << endl;  // 1111111111111111  
}  
```  
  
## <a name="shifts-and-promotions"></a>Przesunięcia i awansowania  
 Wyrażenia po obu stronach operatora przesunięcia muszą być typami całkowitoliczbowymi. Promocje typów całkowitych są wykonywane zgodnie z opisem w temacie regułami [konwersje standardowe](standard-conversions.md). Typ wyniku jest taki sam jak typ awansowana *wyrażenia przesunięcia*.  
  
 W poniższym przykładzie zmienna typu `char` jest podwyższany do `int`.  
  
```cpp  
#include <iostream>  
#include <typeinfo>  
  
using namespace std;  
  
int main() {  
    char char1 = 'a';  
  
    auto promoted1 = char1 << 1;   // 194  
    cout << typeid(promoted1).name() << endl;  // int  
  
    auto promoted2 = char1 << 10;  // 99328  
    cout << typeid(promoted2).name() << endl;  // int  
}  
```  
  
## <a name="additional-details"></a>Dodatkowe szczegóły  
 Wynik operacji shift jest niezdefiniowana, jeśli *dodatku wyrażenie* jest ujemny lub, jeśli *dodatku wyrażenie* jest większa lub równa liczbie bitów w (awansowana)  *wyrażenie SHIFT*. Jeśli to nie przeprowadzono żadnej operacji shift *dodatku wyrażenie* ma wartość 0.  
  
```cpp  
#include <iostream>  
#include <bitset>  
using namespace std;  
  
int main() {  
    unsigned int int1 = 4;  
    bitset<32> b1{int1};  
    cout << b1 << endl;    // 00000000000000000000000000000100  
  
    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior  
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior  
  
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior  
  
    unsigned int int6 = int1 << 0;  
    bitset<32> b6{int6};  
    cout << b6 << endl;    // 00000000000000000000000000000100 (no change)}  
}  
```  
  
## <a name="footnotes"></a>Przypisy dolne  
 1 poniżej przedstawiono opis operatory przesunięcia w języku C ++ 11 ISO specyfikacji (14882-2011[2012]) INCITS/ISO/IEC, sekcje 5.8.2 i 5.8.3.  
  
 Wartość **E1 << E2** jest **E1** przesunięte lewej **E2** bit pozycji; vacated bity są wypełnione zero. Jeśli **E1** ma typ bez znaku, wartość wyniku jest **E1, x 2**<sup>**E2**</sup>, zmniejszenie modulo jeden większa niż wartość maksymalna, można przedstawić w Typ wyniku. W przeciwnym razie, jeśli **E1** typu ze znakiem i wartość nieujemną i **E1, x 2**<sup>**E2** </sup> jest można przedstawić w odpowiedni typ bez znaku następnie typu wyniku tej wartości przekonwertowane na typ wyniku jest wartość wynikową; w przeciwnym razie jest niezdefiniowany.  
  
 Wartość **E1 >> E2** jest **E1** przesunięte prawo **E2** bit pozycji. Jeśli **E1** ma typ bez znaku lub, jeśli **E1** poziomu typu ze znakiem i wartość nieujemną, wartość wyniku jest integralną częścią iloraz **E1/2** <sup> **E2**</sup>. Jeśli **E1** poziomu typu ze znakiem i wartością ujemną, wartość wynikową jest zdefiniowane w implementacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia z operatorami Dwuargumentowymi](../cpp/expressions-with-binary-operators.md)   
 [Wbudowane operatory, pierwszeństwo i kojarzenie języka C++](../cpp/cpp-built-in-operators-precedence-and-associativity.md)