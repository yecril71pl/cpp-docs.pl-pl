---
title: const_seg | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc-pragma.const_seg
- const_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, const_seg
- const_seg pragma
ms.assetid: 1eb58ee2-fb0e-4a39-9621-699c8f5ef957
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c4c87ee9f0e867223186868de0ef2b39203c3710
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="constseg"></a>const_seg
Określa segment gdzie [const](../cpp/const-cpp.md) zmienne są przechowywane w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma const_seg ( [ [ { push | pop}, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.  
  
 Pliki OBJ mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj `const` zmiennych jest .rdata. Niektóre `const` zmienne, takie jak wartości skalarne, są automatycznie wbudowane do strumienia kodu. Kodu wbudowanego nie będą widoczne w .rdata.  
  
 Definiowanie obiektów wymagających inicjacja dynamiczna w `const_seg` powoduje niezdefiniowane zachowanie.  
  
 `#pragma const_seg` Resetuje segmentu .rdata bez parametrów.  
  
 `push` (opcjonalnie)  
 Umieszcza rekord na wewnętrznym stosie kompilatora. A `push` może mieć `identifier` i `segment-name`.  
  
 `pop` (opcjonalnie)  
 Usuwa rekord z góry wewnętrznego stosu kompilatora.  
  
 `identifier` (opcjonalnie)  
 W przypadku użycia z `push`, przypisuje nazwę w rekordzie na stosie wewnętrznych kompilatora. W przypadku użycia z `pop`, POP rejestruje wewnętrzny stosu do `identifier` zostanie usunięta; Jeśli `identifier` nie znaleziono na stosie wewnętrznego, nic nie jest zdjęte ze stosu.  
  
 Przy użyciu `identifier` umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednej `pop` polecenia.  
  
 "`segment-name`" (opcjonalnie)  
 Nazwa segmentu. W przypadku użycia z `pop`, zdjęte ze stosu stosu i `segment-name` staje się nazwa active segmentu.  
  
 "`segment-class`" (opcjonalnie)  
 Uwzględnione w celu zapewnienia zgodności z C++ przed w wersji 2.0. Jest on ignorowany.  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directive_const_seg.cpp  
// compile with: /EHsc  
#include <iostream>  
  
const int i = 7;               // inlined, not stored in .rdata  
const char sz1[]= "test1";     // stored in .rdata  
  
#pragma const_seg(".my_data1")  
const char sz2[]= "test2";     // stored in .my_data1  
  
#pragma const_seg(push, stack1, ".my_data2")  
const char sz3[]= "test3";     // stored in .my_data2  
  
#pragma const_seg(pop, stack1) // pop stack1 from stack  
const char sz4[]= "test4";     // stored in .my_data1  
  
int main() {  
    using namespace std;  
   // const data must be referenced to be put in .obj  
   cout << sz1 << endl;  
   cout << sz2 << endl;  
   cout << sz3 << endl;  
   cout << sz4 << endl;  
}  
```  
  
```Output  
test1  
test2  
test3  
test4  
```  
  
## <a name="comments"></a>Komentarze  
 Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) lista nazw nie należy używać podczas tworzenia sekcji.  
  
 Można również określić sekcjach danymi zainicjowanymi ([data_seg](../preprocessor/data-seg.md)), odinicjowany danych ([bss_seg](../preprocessor/bss-seg.md)), funkcje i ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)