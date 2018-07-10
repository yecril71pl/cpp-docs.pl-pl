---
title: Diagnostyka wydrukowana przez funkcję assert | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2c219669d018dc8c4cb038e90dffd1137877f422
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382880"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert
**ANSI 4.2** dane diagnostyczne drukowanymi przez i zachowanie po przerwaniu dla **assert** — funkcja  
  
 **Assert** komunikatów diagnostycznych i wywołania funkcji drukowane **przerwać** procedury, jeśli wyrażenie ma wartość false (0). Komunikat diagnostycznych ma formularza  
  
 **Nie można potwierdzić**: *wyrażenie ***, plik** *filename ***, linia** *numer wiersza*  
  
 gdzie nazwa pliku jest nazwa pliku źródłowego, a numer wiersza jest numer wiersza to potwierdzenie, że nie powiodło się w pliku źródłowym. Nie podjęto żadnej akcji, jeśli wyrażenie jest prawdziwe (różną od zera).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)