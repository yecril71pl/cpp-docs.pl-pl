---
title: "seed_seq — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
dev_langs: C++
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: de741e8e36f6358b0b0f100eaa266336c0338ca2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="seedseq-class"></a>seed_seq — Klasa
Przechowuje wektor wartości całkowitej bez znaku, zapewniających losowego inicjatora dla aparatu liczb losowych.  
  
## <a name="syntax"></a>Składnia  
```  
class seed_seq  
   {  
public:  
   // types  
   typedef unsigned int result_type;  

   // constructors  
   seed_seq();
   template <class T>  
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>  
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions  
   template <class RandomAccessIterator>  
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions  
   size_t size() const;
   template <class OutputIterator>  
      void param(OutputIterator dest) const;

   // no copy functions  
   seed_seq(const seed_seq&) = delete;  
   void operator=(const seed_seq&) = delete;  
   };  
```  
## <a name="types"></a>Types  
 `typedef unsigned int result_type;`   
Typ elementów sekwencji inicjatora. Typ 32-bitowej liczby całkowitej bez znaku.  
  
## <a name="constructors"></a>Konstruktorów  
 `seed_seq();`   
Domyślny konstruktor inicjuje ma pustą sekwencją wewnętrznego.  
  
 `template<class T>`   
 `seed_seq(initializer_list<T> initlist);`   
Używa `initlist` można ustawić wewnętrzny sekwencji.                   
`T`musi być typu integer.  
  
 `template<class InputIterator>`   
 `seed_seq(InputIterator begin, InputIterator end);`   
Inicjuje sekwencja wewnętrznej przy użyciu wszystkie elementy w zakresie wejściowych iteratora podane.                  
`iterator_traits<InputIterator>::value_type`musi być typu integer.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="generating-functions"></a>Generowanie funkcji  
 `template<class RandomAccessIterator> void generate(RandomAccessIterator begin,          RandomAccessIterator end);`   
Wypełnia elementy sekwencja podana przy użyciu wewnętrznego algorytmu. Ten algorytm wpływ wewnętrzny sekwencji, z którym `seed_seq` został zainicjowany.                          
Nie robi nic, jeśli `begin == end`.  
  
### <a name="property-functions"></a>Funkcje właściwości  
 `size_t size() const;`   
Zwraca liczbę elementów w `seed_seq`.  
  
 `template<class OutputIterator> void param(OutputIterator dest) const;`   
Kopiuje wewnętrzny sekwencji do iteratora dane wyjściowe `dest`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykonuje trzy konstruktory i generuje dane wyjściowe z powstałe w ten sposób `seed_seq` wystąpienia po przypisaniu do tablicy. Na przykład, który używa `seed_seq` generatora liczb losowych zobacz [ \<losowe >](../standard-library/random.md).  
  
```cpp  
#include <iostream>  
#include <random>  
#include <string>  
#include <array>  
  
using namespace std;  
  
void test(const seed_seq& sseq) {  
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;  
  
    cout << "seed_seq::param(): ";  
    ostream_iterator<unsigned int> out(cout, " ");  
    sseq.param(out);  
    cout << endl;  
  
    cout << "Generating a sequence of 5 elements into an array: " << endl;  
    array<unsigned int, 5> seq;  
    sseq.generate(seq.begin(), seq.end());  
    for (unsigned x : seq) { cout << x << endl; }  
}  
  
int main()  
{  
    seed_seq seed1;  
    test(seed1);  
  
    seed_seq seed2 = { 1701, 1729, 1791 };  
    test(seed2);  
  
    string sstr = "A B C D"; // seed string  
    seed_seq seed3(sstr.begin(), sstr.end());  
    test(seed3);  
}  
```  
  
```Output  
seed_seq::size(): 0  
seed_seq::param():  
Generating a sequence of 5 elements into an array:  
505382999  
163489202  
3932644188  
763126080  
73937346  
  
seed_seq::size(): 3  
seed_seq::param(): 1701 1729 1791  
Generating a sequence of 5 elements into an array:  
1730669648  
1954224479  
2809786021  
1172893117  
2393473414  
  
seed_seq::size(): 7  
seed_seq::param(): 65 32 66 32 67 32 68  
Generating a sequence of 5 elements into an array:  
3139879222  
3775111734  
1084804564  
2485037668  
1985355432  
```  
  
## <a name="remarks"></a>Uwagi  
 Funkcje elementów członkowskich tej klasy nie zgłaszają wyjątki.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<losowe >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [\<losowe >](../standard-library/random.md)


