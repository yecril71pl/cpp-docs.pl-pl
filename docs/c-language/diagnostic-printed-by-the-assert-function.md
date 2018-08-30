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
ms.openlocfilehash: 1e824e94f79aa01ab3a82675fb3e8f76059c567d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195555"
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostyka wydrukowana przez funkcję assert
**ANSI 4.2** diagnostyczne drukowanymi przez i zachowanie po przerwaniu dla **asercja** — funkcja  
  
**Asercja** funkcja drukuje komunikat diagnostyczny i wywołania **przerwać** procedury, jeśli wyrażenie ma wartość false (0). Komunikat diagnostyczny ma postać  

> **Nie można potwierdzić**: <em>wyrażenie</em>**, plik** <em>filename</em>**, wiersz** *linenumber*  

gdzie *filename* jest nazwa pliku źródłowego i *linenumber* jest numer wiersza potwierdzenie, że nie powiodło się w pliku źródłowym. Jeśli zostanie podjęta żadna akcja *wyrażenie* ma wartość true (niezerową).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)