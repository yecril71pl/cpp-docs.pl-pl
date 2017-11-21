---
title: bss_seg | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs: C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95fbd0b845bc3e827e2e62c4bd2e97f5cff220d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="bssseg"></a>bss_seg
Określa segment, w którym niezainicjowanych zmiennych są przechowywane w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Pliki obj mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj niezainicjowanych danych jest .bss. W niektórych przypadkach wykorzystania **bss_seg** może załadować razy grupując niezainicjowanych danych w jednej sekcji.  
  
 **bss_seg** bez parametrów resetuje segmentu .bss.  
  
 **wypychania**(opcjonalnie)  
 Umieszcza rekord na wewnętrznym stosie kompilatora. A **wypychania** może mieć *identyfikator* i *nazwą segmentu*.  
  
 **POP** (opcjonalnie)  
 Usuwa rekord z góry wewnętrznego stosu kompilatora.  
  
 *Identyfikator* (opcjonalnie)  
 W przypadku użycia z **wypychania**, przypisuje nazwę w rekordzie na stosie wewnętrznych kompilatora. W przypadku użycia z **pop**, POP rejestruje wewnętrzny stosu do *identyfikator* zostanie usunięta; Jeśli *identyfikator* nie znaleziono na stosie wewnętrznego, nic nie jest zdjęte ze stosu.  
  
 *Identyfikator* umożliwia wielu rekordów zostać zdjęte ze stosu za pomocą jednej **pop** polecenia.  
  
 *"Nazwa segmentu"*(opcjonalnie)  
 Nazwa segmentu. W przypadku użycia z **pop**, zdjęte ze stosu stosu i *nazwą segmentu* staje się nazwa active segmentu.  
  
 *"segmentu klasy"* (opcjonalnie)  
 Uwzględnione w celu zapewnienia zgodności z C++ przed w wersji 2.0. Jest on ignorowany.  
  
## <a name="example"></a>Przykład  
  
```  
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
  
 Można również określić sekcjach danymi zainicjowanymi ([data_seg](../preprocessor/data-seg.md)), funkcje ([code_seg](../preprocessor/code-seg.md)) i zmienne const ([const_seg](../preprocessor/const-seg.md)).  
  
 Przydzielony przy użyciu danych **bss_seg** pragma nie zachowuje żadnych informacji o lokalizacji.  
  
 Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) lista nazw nie należy używać podczas tworzenia sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)