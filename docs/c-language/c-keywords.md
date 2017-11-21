---
title: "Słowa kluczowe języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 71e5c715c6065e8c05466bc3f09eba57606b304e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="c-keywords"></a>Słowa kluczowe języka C
„Słowa kluczowe” to słowa, które mają specjalne znaczenie dla kompilatora C. W fazach translacji 7 i 8 identyfikator nie może mieć tej samej pisowni i wielkości liter co słowo kluczowe C. (Zobacz opis [fazy tłumaczenia](../preprocessor/phases-of-translation.md) w *odwołania preprocesora*; w przypadku informacji na temat identyfikatorów, zobacz [identyfikatory](../c-language/c-identifiers.md).) Język C używa następujących słów kluczowych:  
  
|||||  
|-|-|-|-|  
|**Automatycznie**|**podwójne**|**int**|**— Struktura**|  
|**podział**|**else**|**długa**|**Przełącznik**|  
|**Case**|**wyliczenia**|**Rejestr**|**Element TypeDef**|  
|**char**|**extern**|**Zwraca**|**Unii**|  
|**Const**|**float**|**krótki**|**bez znaku**|  
|**Kontynuuj**|**dla**|**podpisany**|**void**|  
|**domyślne**|**Przejdź do**|**sizeof**|**volatile**|  
|**czy**|**Jeśli**|**statyczne**|**Podczas**|  
  
 Nie można przedefiniować słów kluczowych. Można jednak określić tekst, który można podstawić przed kompilacji za pomocą C [dyrektywy preprocesora](../preprocessor/preprocessor-directives.md).  
  
 **Dotyczące firmy Microsoft**  
  
 Standard ANSI C umożliwia identyfikatorom z dwoma podkreśleniami wiodącymi rezerwację do implementacji kompilatora. Tym samym, konwencja Microsoft zakłada, że podwójne podkreślenie będzie poprzedzało charakterystyczne dla Microsoft słowa kluczowe. Te słowa nie można użyć jako nazwy identyfikatora. Opis ANSI reguły nazewnictwa identyfikatorów, łącznie z użyciem podwójne podkreślenia, zobacz [identyfikatory](../c-language/c-identifiers.md).  
  
 Poniższe słowa kluczowe i specjalne identyfikatory są rozpoznawane przez kompilator Microsoft C:  
  
|||||  
|-|-|-|-|  
|**__asm**|**DllImport**2|**__int8**|**naked**2|  
|**__based**1|**__except**|**__int16**|**__stdcall**|  
|**__cdecl**|**__fastcall**|**__int32**|**Wątek**2|  
|**__declspec**|**__finally**|**__int64**|**__try**|  
|**dllexport**2|**__inline**|**__leave**||  
  
 1. **__Based** — słowo kluczowe ma ograniczoną zastosowania kompilacje docelowym 32-bitowe i 64-bitowych.  
  
 2. Są to specjalne identyfikatory, gdy jest używany z **__declspec**; ich użycie w innych kontekstach nie jest ograniczona.  
  
 Rozszerzenia Microsoft są domyślnie włączone. Aby upewnić się, że Twoje programy są w pełni zgodne, możesz wyłączyć rozszerzenia Microsoft określając opcję wiersza polecenia /Za (kompiluj dla zgodności ANSI) podczas kompilacji. Gdy to zrobisz, słowa kluczowe specyficzne dla firmy Microsoft są wyłączone.  
  
 Po włączeniu rozszerzeń Microsoft, możesz używać słów kluczowych wymienionych powyżej w swoich programach. W celu zachowania zgodności z ANSI, większość słów kluczowych jest poprzedzona podwójnym podkreśleniem. Cztery wyjątki **dllexport**, **dllimport**, **naked**, i **wątku**, są używane tylko z **__declspec** i w związku z tym nie wymagają wiodące podwójnego znaku podkreślenia. W celu zapewnienia zgodności z poprzednimi wersjami, wersje z pojedynczym podkreśleniem reszty słów kluczowych są obsługiwane.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy języka C](../c-language/elements-of-c.md)