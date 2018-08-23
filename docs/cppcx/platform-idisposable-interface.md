---
title: Platform::IDisposable, interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3899c25d71ad08cc058280271080c19d11222ed
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589789"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable, interfejs
Używane, aby zwolnić niezarządzane zasoby.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>Atrybuty  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>Elementy członkowskie  
 Interfejs IDisposable dziedziczy po interfejsie IUnknown. Interfejs IDisposable ma również następujące rodzaje składowych:  
  
 **Metody**  
  
 Interfejs IDisposable, ma następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|Metody Dispose|Używane, aby zwolnić niezarządzane zasoby.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy