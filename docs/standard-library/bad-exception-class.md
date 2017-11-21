---
title: Klasa bad_exception | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: exception/std::bad_exception
dev_langs: C++
helpviewer_keywords: bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3a322ce0ed9621e1413009092b0afb9572196a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="badexception-class"></a>Klasa bad_exception
Klasa opisuje wyjątek, który może zostać wygenerowany z nieoczekiwany obsługi.  
  
## <a name="syntax"></a>Składnia  
  
```  
class bad_exception    : public exception {};  
```  
  
## <a name="remarks"></a>Uwagi  
 [Nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłosi `bad_exception` zamiast przerywa lub zamiast kontaktować się z inną funkcję określony za pomocą [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) Jeśli `bad_exception` jest uwzględniony na liście throw funkcji.  
  
 Wartość zwrócona przez **co** to ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.  
  
 Aby uzyskać listę członków dziedziczonych przez `bad_exception` , zobacz [wyjątek klasy](../standard-library/exception-class.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [set_unexpected —](../standard-library/exception-functions.md#set_unexpected) na przykład użycie [nieoczekiwany](../standard-library/exception-functions.md#unexpected) zgłaszanie `bad_exception`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<wyjątku >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
[wyjątek klasy](../standard-library/exception-class.md) [bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

