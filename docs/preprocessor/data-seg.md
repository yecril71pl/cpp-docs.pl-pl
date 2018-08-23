---
title: data_seg | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
dev_langs:
- C++
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1be97919f0f5b55d6e63eca8e59eb15e8ef9dff
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466416"
---
# <a name="dataseg"></a>data_seg
Określa segment danych, gdzie zainicjowane zmienne są przechowywane w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi 

Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.  
  
Pliki OBJ mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj zainicjowane zmiennych jest .data. Niezainicjowane zmienne są traktowane jako być inicjowane od zera i są przechowywane w .bss.  
  
**data_seg** bez parametrów resetuje segmentu .data.  
  
*wypychane* (opcjonalnie)  
Umieszcza rekord na wewnętrznym stosie kompilatora. A *wypychania* może mieć *identyfikator* i *nazwą segmentu*.  
  
*POP* (opcjonalnie)  
Usuwa rekord z góry wewnętrznego stosu kompilatora.  
  
*Identyfikator* (opcjonalnie)  
Gdy jest używane z *wypychania*, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. Gdy jest używane z *pop*, zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zostanie zdjęte.  
  
*Identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednego *pop* polecenia.  
  
*"segment-name"*(opcjonalnie)  
Nazwa segmentu. Gdy jest używane z *pop*, stos jest zdejmowany i *nazwą segmentu* staje się nazwą aktywny segment.  
  
*"klasy segmentu"* (opcjonalnie)  
Uwzględnione na potrzeby utrzymywania zgodności z C++ wcześniejszych niż 2.0. Jest on ignorowany.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// pragma_directive_data_seg.cpp  
int h = 1;                     // stored in .data  
int i = 0;                     // stored in .bss  
#pragma data_seg(".my_data1")  
int j = 1;                     // stored in "my_data1"  
  
#pragma data_seg(push, stack1, ".my_data2")     
int l = 2;                     // stored in "my_data2"  
  
#pragma data_seg(pop, stack1)   // pop stack1 off the stack  
int m = 3;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
Danych przydzielonych przy użyciu **data_seg** nie zachowuje żadnych informacji o lokalizacji.  
  
Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) listę nazw, nie należy używać podczas tworzenia sekcji.  
  
Można również określić sekcje dla zmiennych const ([const_seg](../preprocessor/const-seg.md)), niezainicjowanych danych ([bss_seg](../preprocessor/bss-seg.md)) i funkcje ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)