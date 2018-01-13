---
title: "future_error — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: future/std::future_error
dev_langs: C++
ms.assetid: 6071c545-ac2a-49ef-9967-07b0125da861
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1fc5ba9a34ee5c1a29892e4ba6ebc25366e408be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="futureerror-class"></a>future_error — Klasa
Opisuje obiekt wyjątku, który może zostać wygenerowany przez metody typów, które zarządzają [przyszłych](../standard-library/future-class.md) obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```
class future_error : public logic_error {
public:
    future_error(error_code code);

const error_code& code() const throw();

const char *what() const throw();

};
```  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<przyszłych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [logic_error — klasa](../standard-library/logic-error-class.md)   
 [error_code, klasa](../standard-library/error-code-class.md)
