---
title: Platform::ValueType, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 12766e81ddd90b257830b6bf5adefd2562781d9e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43767767"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType, klasa
Klasa bazowa dla wystąpień typów wartości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Zwraca reprezentację ciągu obiektu. Odziedziczone po [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Uwagi  
 Klasa ValueType jest używana do tworzenia typów wartości. Element ValueType pochodzi z obiektu, który zawiera podstawowe składniki. Jednak kompilator odłącza tych podstawowych członków z typów wartości, które pochodzą z klasy ValueType. Kompilator ponowne dołączenie następuje ponowne tych podstawowych elementów członkowskich, gdy typ wartości jest spakowany.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

## <a name="tostring"></a> Metoda ValueType::ToString
Zwraca reprezentację ciągu obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Platform::String, który reprezentuje wartość.  
    
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)