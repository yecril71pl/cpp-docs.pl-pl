---
title: "Tłumaczenie: Diagnostyka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb7f826be88ebec640a6f3b40b38478eea91ed36
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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