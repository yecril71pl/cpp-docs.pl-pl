---
title: Klasa platform::ValueType | Dokumentacja firmy Microsoft
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1994aa6445c67bae138a51f1d3eebb2a54f9b17d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="platformvaluetype-class"></a>Klasa platform::ValueType
Klasa podstawowa dla wystąpień typów wartości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class ValueType : Object  
```  
  
## <a name="public-methods"></a>Metody publiczne  
  
|||  
|-|-|  
|[ValueType::ToString](#tostring)|Zwraca reprezentację ciągu obiektu. Dziedziczone z [Platform::Object](../cppcx/platform-object-class.md).|  
  
### <a name="remarks"></a>Uwagi  
 Klasa ValueType jest używana do tworzenia typów wartości. Element ValueType pochodzi z obiektu, który zawiera podstawowe składniki. Jednak kompilator odłącza te podstawowe elementy członkowskie z typów wartości, które są pochodnymi klasy ValueType. Kompilator reattaches tych podstawowych elementów członkowskich, gdy typ wartości jest opakowany.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

## <a name="tostring"></a> ValueType::ToString — metoda
Zwraca reprezentację ciągu obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::String ToString();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Platform::String, który reprezentuje wartość.  
    
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)