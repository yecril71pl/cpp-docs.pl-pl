---
title: Identyfikator UUID (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e81b81509877ff53b613af80638b2386ed0cb0b2
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37948224"
---
# <a name="uuid-c"></a>uuid (C++)
**Microsoft Specific**  
  
 Kompilator dołącza identyfikator GUID do klasy lub struktury zadeklarowane lub zdefiniowane (pełna COM definicje obiektów tylko) za pomocą **uuid** atrybutu.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>Uwagi  
 **Uuid** atrybut przyjmuje ciąg jako argumentem. Ten ciąg nazwy identyfikatora GUID w formacie normalne rejestru z lub bez **{}** ograniczników. Na przykład:  
  
```cpp 
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Ten atrybut można stosować w ponowna deklaracja. Dzięki temu nagłówki systemu, aby dostarczyć definicje interfejsów, takich jak `IUnknown`i ponowna deklaracja niektórych innych nagłówka (takie jak \<comdef.h >) umożliwiają określanie wartości identyfikatora GUID.  
  
 Słowo kluczowe [__uuidof](../cpp/uuidof-operator.md) mogą być stosowane do pobrania — stała identyfikator GUID jest dołączony do typu zdefiniowanego przez użytkownika.  
  
 **END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)