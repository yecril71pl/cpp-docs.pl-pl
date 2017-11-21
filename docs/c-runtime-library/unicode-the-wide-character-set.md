---
title: "Unicode: Zestaw znaków dwubajtowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.international
dev_langs: C++
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5683cb5b161fd492afc69a93b6779b16c19c4022
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-the-wide-character-set"></a>Unicode: zestaw znaków dwubajtowych
Znaków dwubajtowych jest kodem 2-bajtowych wartości znakowych wielu języków. Dowolny znak używany w przypadku nowoczesnych komputerów na całym świecie, tym techniczne symboli i znaków specjalnych publikowania, może być reprezentowany według specyfikacji Unicode jako znaków dwubajtowych. Opracowany i aktualizowany przez dużych konsorcjum zawierającą firmy Microsoft, standardu Unicode teraz jest powszechnie zaakceptowany.  
  
 Typ jest znaków dwubajtowych `wchar_t`. Ciąg znaków dwubajtowych jest reprezentowany jako `wchar_t[]` tablicy i jest wskazywana przez `wchar_t*` wskaźnika. Jako znaków dwubajtowych może reprezentować znaków ASCII, dodając literę `L` do znaku. Na przykład L '\0' to przerywanie dwubajtowe (16-bitowy) `NULL` znaków. Podobnie może reprezentować dowolny ciąg ASCII literałów jako literału ciągu znaków dwubajtowych po prostu dodając litera na literał ASCII (L "Hello").  
  
 Ogólnie rzecz biorąc znaki dwubajtowe zajmują więcej miejsca w pamięci niż znaków wielobajtowych, ale są szybsze do procesu. Ponadto tylko jeden ustawień regionalnych może być reprezentowany w czasie w kodowaniu wielobajtowe, natomiast zestawy wszystkich znaków w świecie są jednocześnie reprezentowane przez reprezentacja Unicode.  
  
## <a name="see-also"></a>Zobacz też  
 [Przystosowywanie do warunków międzynarodowych](../c-runtime-library/internationalization.md)   
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)