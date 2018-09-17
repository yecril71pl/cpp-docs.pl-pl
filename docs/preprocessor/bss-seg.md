---
title: bss_seg | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c3a80e50bd0b012773a5e5a197674965f73b526
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711161"
---
# <a name="bssseg"></a>bss_seg
Określa segment, w którym niezainicjowane zmienne są przechowywane w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi  

Pliki obj mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj, niezainicjowanych danych jest .bss. W niektórych przypadkach użycie **bss_seg** można przyspieszyć czasów ładowania przez grupowanie niezainicjowanych danych w jednej sekcji.  
  
**bss_seg** bez parametrów resetuje segmentu .bss.  
  
**push**<br/>
(Opcjonalnie) Umieszcza rekord na wewnętrznym stosie kompilatora. A *pu*sh * może mieć *identyfikator* i *nazwą segmentu*.  
  
**POP**<br/>
(Opcjonalnie) Usuwa rekord z góry wewnętrznego stosu kompilatora.  
  
*Identyfikator*<br/>
(Opcjonalnie) Gdy jest używane z **wypychania**, przypisuje nazwę rekordowi na wewnętrznym stosie kompilatora. Gdy jest używane z **pop**, zdejmuje rekordy z wewnętrznego stosu aż do usunięcia *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie zostanie znaleziony na wewnętrznym stosie, nic nie zostanie zdjęte.  
  
*Identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednego **pop** polecenia.  
  
*"segment-name"*<br/>
(Opcjonalnie) Nazwa segmentu. Gdy jest używane z **pop**, stos jest zdejmowany i *nazwą segmentu* staje się nazwą aktywny segment.  
  
*"segmentu class"*<br/>
(Opcjonalnie) Uwzględnione na potrzeby utrzymywania zgodności z C++ wcześniejszych niż 2.0. Jest on ignorowany.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// pragma_directive_bss_seg.cpp  
int i;                     // stored in .bss  
#pragma bss_seg(".my_data1")  
int j;                     // stored in "my_data1"  
  
#pragma bss_seg(push, stack1, ".my_data2")     
int l;                     // stored in "my_data2"  
  
#pragma bss_seg(pop, stack1)   // pop stack1 from stack  
int m;                     // stored in "stack_data1"  
  
int main() {  
}  
```  
  
Można również określić sekcje dla danych zainicjowanych ([data_seg](../preprocessor/data-seg.md)), funkcje ([code_seg](../preprocessor/code-seg.md)) i zmiennych const ([const_seg](../preprocessor/const-seg.md)).  
  
Danych przydzielonych przy użyciu **bss_seg** pragma nie zachowuje żadnych informacji o lokalizacji.  
  
Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) listę nazw, nie należy używać podczas tworzenia sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)