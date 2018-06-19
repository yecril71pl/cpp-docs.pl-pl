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
ms.openlocfilehash: 7a463d966c681557525bb9512762731c01a7ce30
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841235"
---
# <a name="dataseg"></a>data_seg
Określa, gdzie zainicjowane zmienne są przechowywane w pliku .obj segmentu danych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma data_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.  
  
 Pliki OBJ mogą być wyświetlane z [dumpbin](../build/reference/dumpbin-command-line.md) aplikacji. Segment domyślnej w pliku .obj zainicjowane zmiennych jest .data. Zmienne, które są niezainicjowanej są traktowane jako, aby można było zainicjować od zera i są przechowywane w .bss.  
  
 **data_seg** bez parametrów resetuje segmentu .data.  
  
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
  
 Przydzielony przy użyciu danych **data_seg** nie zachowuje żadnych informacji o lokalizacji.  
  
 Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) lista nazw nie należy używać podczas tworzenia sekcji.  
  
 Można również określić sekcji zmiennych const ([const_seg](../preprocessor/const-seg.md)), odinicjowany danych ([bss_seg](../preprocessor/bss-seg.md)), funkcje i ([code_seg](../preprocessor/code-seg.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)