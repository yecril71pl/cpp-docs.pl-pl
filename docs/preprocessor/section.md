---
title: sekcja | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- section_CPP
- vc-pragma.section
dev_langs: C++
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc6035caeb3b2fe466d18ea92300b3135a6189f0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
  
 `attributes`opcjonalny parametr składający się z co najmniej jeden przecinkami atrybutów, które chcesz przypisać do sekcji. Możliwe `attributes` są:  
  
 **read**  
 Zezwala na operacje odczytu danych.  
  
 **write**  
 Zezwala na wykonywanie operacji zapisu na danych.  
  
 **wykonanie**  
 Umożliwia wykonanie kodu.  
  
 **udostępnione**  
 Udostępnia sekcji między wszystkie procesy, które załadowania obrazu.  
  
 **nopage**  
 Oznacza sekcji jako nie stronicowalnej; przydatne dla sterowników urządzeń Win32.  
  
 **NoCache**  
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