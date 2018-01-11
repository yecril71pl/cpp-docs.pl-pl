---
title: code_seg | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
dev_langs: C++
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 35ead52e9e084eb1770e3532d15848e168d8af90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="codeseg"></a>code_seg
Określa segment tekstu, w którym funkcje są przechowywane w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )  
```  
  
## <a name="remarks"></a>Uwagi  
 `code_seg` Dyrektywa pragma nie kontroluje umieszczania kod obiektu wygenerowany dla wystąpień szablonów ani kod niejawnie wygenerowany przez kompilator — na przykład specjalnych funkcji Członkowskich. Firma Microsoft zaleca użycie [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) zamiast tego atrybutu, ponieważ można kontrolować umieszczania cały kod obiektu. Obejmuje to kod wygenerowany przez kompilator.  
  
 A *segmentu* w .obj plik jest nazwane bloku danych, który jest ładowany do pamięci jako jednostka. A *segment tekstu* jest segment, który zawiera kod wykonywalny. W tym artykule warunki *segmentu* i *sekcji* są używane zamiennie.  
  
 `code_seg` Dyrektywa pragma informuje kompilator, aby umieścić cały kod obiektu kolejnych z jednostce tłumaczenia w segmentem tekstu o nazwie `segment-name`. Domyślnie segment tekstu używany dla funkcji w pliku .obj ma nazwę .text.  
  
 A `code_seg` dyrektywa pragma bez parametrów resetuje nazwę segment tekstu kod obiektu kolejnych .text.  
  
 **Wypychanie** (opcjonalnie)  
 Umieszcza rekord na wewnętrznym stosie kompilatora. A **wypychania** może mieć `identifier` i `segment-name`.  
  
 **POP** (opcjonalnie)  
 Usuwa rekord z góry wewnętrznego stosu kompilatora.  
  
 `identifier`(opcjonalnie)  
 W przypadku użycia z **wypychania**, przypisuje nazwę w rekordzie na stosie wewnętrznych kompilatora. W przypadku użycia z **pop**, POP rejestruje wewnętrzny stosu do `identifier` zostanie usunięta; Jeśli `identifier` nie znaleziono na stosie wewnętrznego, nic nie jest zdjęte ze stosu.  
  
 `identifier`Umożliwia wielu rekordów zostać zdjęte ze stosu z tylko jednym **pop** polecenia.  
  
 "`segment-name`" (opcjonalnie)  
 Nazwa segmentu. W przypadku użycia z **pop**, zdjęte ze stosu stosu i `segment-name` staje się nazwą segmentu aktywnego tekstu.  
  
 "`segment-class`" (opcjonalnie)  
 Ignorowanie, ale włączone dla zachowania zgodności z C++ w wersji wcześniejszej niż wersja 2.0.  
  
 Można użyć [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) aplikacji, aby wyświetlić pliki .obj. Wersje DUMPBIN dla każdej architektury docelowej są dołączone [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób użycia `code_seg` dyrektywa pragma do formantu, którym jest umieszczany kod obiektu:  
  
```  
// pragma_directive_code_seg.cpp  
void func1() {                  // stored in .text  
}  
  
#pragma code_seg(".my_data1")  
void func2() {                  // stored in my_data1  
}  
  
#pragma code_seg(push, r1, ".my_data2")  
void func3() {                  // stored in my_data2  
}  
  
#pragma code_seg(pop, r1)      // stored in my_data1  
void func4() {  
}  
  
int main() {  
}  
```  
  
 Aby uzyskać listę nazw, które nie powinny być używane do tworzenia sekcji, zobacz [/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 Można również określić sekcjach danymi zainicjowanymi ([data_seg](../preprocessor/data-seg.md)), odinicjowany danych ([bss_seg](../preprocessor/bss-seg.md)) i zmienne const ([const_seg](../preprocessor/const-seg.md)).  
  
## <a name="see-also"></a>Zobacz też  
 [code_seg (__declspec)](../cpp/code-seg-declspec.md)   
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)