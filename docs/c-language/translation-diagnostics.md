---
title: "Tłumaczenie: Diagnostyka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10349357fa0411357b702ff48ff9407c1f5b91e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="translation-diagnostics"></a>Tłumaczenie: diagnostyka
**ANSI 2.1.1.3** jak określono diagnostyki  
  
 Microsoft C tworzy komunikaty o błędach w postaci:  
  
```  
  
filename( line-number ) : diagnostic Cnumbermessage  
```  
  
 gdzie *filename* to nazwa pliku źródłowego, w którym wystąpił błąd; *numer wiersza* jest numer wiersza, w którym kompilator wykrył błąd; `diagnostic` "error" lub "ostrzeżenie"; `number` to unikatowy numer czterocyfrowe (poprzedzone **C**, zgodnie z opisem w składni), które identyfikują błąd lub ostrzeżenie; `message` jest komunikat z wyjaśnieniem.  
  
## <a name="see-also"></a>Zobacz też  
 [Zachowanie zdefiniowane w implementacji](../c-language/implementation-defined-behavior.md)