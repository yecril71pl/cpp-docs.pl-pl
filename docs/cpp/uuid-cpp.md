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
ms.openlocfilehash: 93ae3ac7f0d6fff700e1c89aad197d5f03734cf5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467111"
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
  
## <a name="see-also"></a>Zobacz także  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)