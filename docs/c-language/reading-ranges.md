---
title: Odczytywanie zakresów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ebad4bfda77238ad8c861410e2af5453df73af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383647"
---
# <a name="reading-ranges"></a>Odczytywanie zakresów
**ANSI 4.9.6.2** interpretacji znak kreski (-), który jest ani pierwszym ani ostatnim znakiem w scanlist % [konwersja w `fscanf` — funkcja  
  
 Następujący wiersz  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 odczytuje dowolną liczbę znaków z zakresu A-Z w ciągu do której `strptr` punktów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)