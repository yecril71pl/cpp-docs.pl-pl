---
title: '&lt;ccomplex&gt; | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <ccomplex>
dev_langs: C++
ms.assetid: a9fcb5f0-88e3-464b-a5fd-d1afb8cd7e6f
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c381a68e913be77a1d62dc0f90fecdca9ee8d226
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltccomplexgt"></a>&lt;ccomplex&gt;
Zawiera nagłówek standardowa biblioteka C++ [ \<złożonych >](../standard-library/complex.md), w tym skutecznie nagłówka biblioteki standardowe C \<complex.h > i dodaje skojarzone nazwy `std` przestrzeni nazw.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#include <ccomplex>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Ten nagłówek w tym zapewnia, że nazwy zadeklarowane za pomocą zewnętrznego powiązania w nagłówku biblioteki standardowe C są zadeklarowane w `std` przestrzeni nazw.  
  
 Nazwa `clog`, która jest zadeklarowana w \<complex.h >, nie jest zdefiniowany w `std` przestrzeni nazw z powodu potencjalnych konfliktów z `clog` zadeklarowanego w [ \<iostream >](../standard-library/iostream.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Standardowa biblioteka C++ — przegląd](../standard-library/cpp-standard-library-overview.md)



