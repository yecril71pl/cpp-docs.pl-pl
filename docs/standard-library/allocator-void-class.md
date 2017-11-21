---
title: Program przydzielania&lt;void&gt; klasy | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
dev_langs: C++
helpviewer_keywords: allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e1d9ddd5c719bffe8fec9c77c3495e7d170eaeb0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="allocatorltvoidgt-class"></a>Program przydzielania&lt;void&gt; — klasa
Specjalizacja szablonu alokatora klasy na typ `void`, definiowanie typów, które sensu, w tym kontekście.  
  
## <a name="syntax"></a>Składnia  
  
```
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa jawnie specjalizuje się klasy szablonu [alokatora](../standard-library/allocator-class.md) dla typu *void.* Operator przypisania and konstruktorów zachowanie takie same jak w przypadku klasy szablonu, ale definiuje on tylko następujących typów:  
  
- [const_pointer](../standard-library/allocator-class.md#const_pointer).  
  
- [wskaźnik](../standard-library/allocator-class.md#pointer).  
  
- [value_type](../standard-library/allocator-class.md#value_type).  
  
- [ponownie powiązać](../standard-library/allocator-class.md#rebind), zagnieżdżone klasy szablonu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<pamięci >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



