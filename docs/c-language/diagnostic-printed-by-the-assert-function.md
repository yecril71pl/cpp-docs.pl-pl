---
title: "Diagnostyka wydrukowana przez funkcję assert | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 243956f1d85b07b5d5b810ebfd112b2cbfe16242
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert
**ANSI 4.2** dane diagnostyczne drukowanymi przez i zachowanie po przerwaniu dla **assert** — funkcja  
  
 **Assert** komunikatów diagnostycznych i wywołania funkcji drukowane **przerwać** procedury, jeśli wyrażenie ma wartość false (0). Komunikat diagnostycznych ma formularza  
  
 **Nie można potwierdzić**: *wyrażenie***, plik** *filename***, wiersz** *numer wiersza*  
  
 gdzie nazwa pliku jest nazwa pliku źródłowego, a numer wiersza jest numer wiersza to potwierdzenie, że nie powiodło się w pliku źródłowym. Nie podjęto żadnej akcji, jeśli wyrażenie jest prawdziwe (różną od zera).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)