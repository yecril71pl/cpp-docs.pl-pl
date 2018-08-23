---
title: Klasa wartości platform::GUID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Guid
dev_langs:
- C++
helpviewer_keywords:
- Platform::Guid Struct
ms.assetid: 25c0bfb2-7f93-44d8-bdf4-ef4fbac3424a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 102585cf7148923f584591102712278847ee7573
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601257"
---
# <a name="platformguid-value-class"></a>Klasa wartości Platform::Guid
Reprezentuje [GUID](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx) typu w systemie typów środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public value struct Guid  
```  
  
### <a name="members"></a>Elementy członkowskie  
 Identyfikator GUID ma metodę Equals, element GetHashCode(), i metody ToString() pochodną [Platform::Object, klasa](../cppcx/platform-object-class.md), i metoda GetTypeCode() pochodnych [Platform::Type, klasa](../cppcx/platform-type-class.md). Identyfikator GUID ma również następujące elementy członkowskie.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[Identyfikator GUID](#ctor)|Inicjuje nowe wystąpienie struktury identyfikatora Guid.|  
|[operator==](#operator-equality)|Operator równości.|  
|[operator!=](#operator-not-equal)|Nie równa się operatora.|  
|[operator()](#operator-call)|Konwertuje identyfikator Guid identyfikatora GUID.|  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać przykład sposobu generowania nowych Platform::Guid, przy użyciu funkcji Windows [funkcji CoCreateGuid](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateguid), zobacz [składnika WinRT: sposób generowania identyfikatora GUID?](http://blogs.msdn.com/b/eternalcoding/archive/2013/03/25/winrt-component-how-to-generate-a-guid.aspx)  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

 
## <a name="ctor"></a> Konstruktory GUID::GUID
Inicjuje nowe wystąpienie struktury identyfikatora Guid.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        unsigned char d,   
        unsigned char e,   
        unsigned char f,   
        unsigned char g,   
        unsigned char h,   
        unsigned char i,   
        unsigned char j,   
        unsigned char k  );  
  
    Guid(GUID m);  
  
    Guid(  
        unsigned int a,   
        unsigned short b,   
        unsigned short c,   
        Array<unsigned char>^ n );  
```  
  
### <a name="parameters"></a>Parametry  
 `a`  
 Pierwsze 4 bajty identyfikatora GUID.  
  
 `b`  
 Następne 2 bajty identyfikatora GUID.  
  
 `c`  
 Następne 2 bajty identyfikatora GUID.  
  
 `d`  
 Następny bajt identyfikatora GUID.  
  
 `e`  
 Następny bajt identyfikatora GUID.  
  
 `f`  
 Następny bajt identyfikatora GUID.  
  
 `g`  
 Następny bajt identyfikatora GUID.  
  
 `h`  
 Następny bajt identyfikatora GUID.  
  
 `i`  
 Następny bajt identyfikatora GUID.  
  
 `j`  
 Następny bajt identyfikatora GUID.  
  
 `k`  
 Następny bajt identyfikatora GUID.  
  
 `m`  
 Identyfikator GUID, zgodnie z definicją.  
  
 `n`  
 8 bajtów pozostałych identyfikatora GUID.  
  

## <a name="operator-equality"></a> GUID::operator == — Operator
Porównuje dwa identyfikatory GUID.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::Guid::operator==  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość true, jeśli dwa identyfikatory GUID są takie same.

## <a name="operator-inequality"></a> GUID::operator! = — Operator
Porównuje dwa identyfikatory GUID.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::Guid::operator!=  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość true, jeśli dwa identyfikatory GUID nie są równe.



## <a name="operator-call"></a> GUID::operator() Operator
Niejawnie konwertuje [identyfikator GUID struktury](http://msdn.microsoft.com/library/windows/desktop/aa373931\(v=vs.85\).aspx)identyfikator GUID służący do Platform::Guid.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
Platform::Guid operator()  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Struktura identyfikatora Guid.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)