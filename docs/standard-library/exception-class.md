---
title: "wyjątek klasy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 24aa11044218257b3471e2d65fe652ca32d39196
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="exception-class"></a>Klasa exception
Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłoszonych przez niektórych wyrażeń i standardowa biblioteka C++.  
  
## <a name="syntax"></a>Składnia  
```  
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };  
``` 
## <a name="remarks"></a>Uwagi  
 W szczególności ta klasa podstawowa jest katalogiem głównym standardowe wyjątek klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md). Wartość zwrócona przez ciąg C `what` jest określony przez konstruktora domyślnego, ale może być zdefiniowana przez konstruktorów niektórych klas pochodnych jako ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.  
  
 `int` Parametr umożliwia określenie, czy można przydzielić pamięci. Wartość `int` jest ignorowana.  
  
> [!NOTE]
>  Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzenia Microsoft do standardowej biblioteki C++.  
  
## <a name="example"></a>Przykład  
 Przykłady użycia klasy standardowe wyjątków, które dziedziczą z `exception` , zobacz jedną z klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<wyjątku >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



