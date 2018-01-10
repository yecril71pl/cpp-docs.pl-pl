---
title: "space_info — struktura | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: filesystem/std::tr2::sys::space_info
dev_langs: C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50657e33becd0fb2dae94d515f82120d6a71e342
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="spaceinfo-structure"></a>space_info — Struktura
Przechowuje informacje o woluminie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`unsigned long long available`|Przedstawia liczbę bajtów, które są dostępne do reprezentowania danych na woluminie.|  
|`unsigned long long capacity`|Reprezentuje całkowita liczba bajtów reprezentujących woluminu.|  
|`unsigned long long free`|Przedstawia liczbę bajtów, które nie są używane do reprezentowania danych na woluminie.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<filesystem >  
  
 **Namespace:** std::experimental::filesystem  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<FileSystem >](../standard-library/filesystem.md)   
 [miejsca](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)   
 [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)

