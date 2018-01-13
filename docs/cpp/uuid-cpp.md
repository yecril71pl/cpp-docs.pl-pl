---
title: Identyfikator UUID (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: uuid_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad4362b8e84d7ffb4bb090a4e513538cdb26ae25
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="uuid-c"></a>uuid (C++)
**Dotyczące firmy Microsoft**  
  
 Kompilator dołącza identyfikatora GUID do klasy lub struktury zadeklarowane lub zdefiniowane (pełna COM definicji obiektu tylko) z `uuid` atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
__declspec( uuid("  
ComObjectGUID  
") ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 `uuid` Atrybut przyjmuje ciąg jako jej argument. Ten ciąg nazwy identyfikatora GUID w formacie normalne rejestru lub bez **{}** ograniczników. Na przykład:  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Ten atrybut można stosować w deklaracji. Dzięki temu nagłówków systemu, aby podać definicje interfejsów, takich jak **IUnknown**i ponowna deklaracja niektórych nagłówka, (na przykład COMDEF. H), aby podać identyfikator GUID.  
  
 Słowo kluczowe [__uuidof](../cpp/uuidof-operator.md) można zastosować do pobrania stała GUID dołączony do typu zdefiniowanego przez użytkownika.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)