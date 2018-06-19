---
title: sekcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs:
- C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8d113c10ea8370a46560ba8668546c74b19c6f8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849945"
---
# <a name="section"></a>sekcja
Tworzy sekcję w pliku .obj.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma section( "section-name" [, attributes] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Znaczenie terminów *segmentu* i *sekcji* są wymienne, w tym temacie.  
  
 Po zdefiniowaniu sekcji pozostaje ważny w pozostałej części kompilacji. Jednak należy użyć [__declspec(allocate)](../cpp/allocate.md) lub nic nie zostanie umieszczona w sekcji.  
  
 *Nazwa sekcji* jest wymaganym parametrem, który ma być nazwę sekcji. Nazwa nie może powodować konfliktu z żadną nazwą standardowej sekcji. Zobacz [/SECTION](../build/reference/section-specify-section-attributes.md) lista nazw nie należy używać podczas tworzenia sekcji.  
  
 `attributes` opcjonalny parametr składający się z co najmniej jeden przecinkami atrybutów, które chcesz przypisać do sekcji. Możliwe `attributes` są:  
  
 **read**  
 Zezwala na operacje odczytu danych.  
  
 **write**  
 Zezwala na wykonywanie operacji zapisu na danych.  
  
 **execute**  
 Umożliwia wykonanie kodu.  
  
 **udostępnione**  
 Udostępnia sekcji między wszystkie procesy, które załadowania obrazu.  
  
 **nopage**  
 Oznacza sekcji jako nie stronicowalnej; przydatne dla sterowników urządzeń Win32.  
  
 **nocache**  
 Oznacza sekcji jako nie buforowalnej; przydatne dla sterowników urządzeń Win32.  
  
 **Odrzuć**  
 Oznacza sekcji jako discardable; przydatne dla sterowników urządzeń Win32.  
  
 **remove**  
 Oznacza sekcji jako nie rezydentny; sterowniki urządzeń wirtualnych (V*x*D) tylko.  
  
 Jeśli nie określisz atrybuty, sekcji będzie mieć odczytu i zapisu atrybutów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pierwszej instrukcji, która identyfikuje sekcji i jego atrybuty. Liczba całkowita `j` nie są umieszczane w `mysec` , ponieważ nie został zadeklarowany z `__declspec(allocate)`; `j` przechodzi w sekcji danych. Liczba całkowita `i` przejdź do `mysec` w jego `__declspec(allocate)` atrybuty klasy magazynu.  
  
```  
// pragma_section.cpp  
#pragma section("mysec",read,write)  
int j = 0;  
  
__declspec(allocate("mysec"))  
int i = 0;  
  
int main(){}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)