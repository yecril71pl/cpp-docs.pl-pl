---
title: 'Tłumaczenie: Diagnostyka | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c6a59abc48e5a6bc2aa727508b61abe120c8425
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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