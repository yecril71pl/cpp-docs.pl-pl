---
title: "Klasa wartości platform::IntPtr | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
dev_langs: C++
helpviewer_keywords: Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 787e8aaa0dc46a651fc4d0ac8b16d9521aebd010
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="platformintptr-value-class"></a>Klasa wartości Platform::IntPtr
Reprezentuje podpisem wskaźnika lub dojścia i którego rozmiar jest specyficzne dla platformy (32-bitowy lub 64-bitowe).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public value struct IntPtr  
```  
  
### <a name="members"></a>Elementy członkowskie  
 IntPtr zawiera następujące elementy:  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|[IntPtr::IntPtr](#ctor)|Inicjuje nowe wystąpienie klasy IntPtr.|  
|[IntPtr::op_explicit — Operator](#op-explicit)|Konwertuje określony parametr typu IntPtr lub wskaźnik do wartości IntPtr.|  
|[IntPtr::ToInt32](#toint32)|Konwertuje bieżący IntPtr 32-bitową liczbę całkowitą.|  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  

## <a name="ctor"></a> IntPtr::IntPtr — Konstruktor
Inicjuje nowe wystąpienie klasy IntPtr o określonej wartości.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );  
```  
  
### <a name="parameters"></a>Parametry  
 value  
 Dojście 64-bitowych lub wskaźnika lub wskaźnik do wartości 64-bitowy lub 32-bitową wartość, który można przekonwertować na wartość 64-bitowa.  
  


## <a name="op-explicit"></a> IntPtr::op_explicit — Operator
Konwertuje określony parametr typu IntPtr lub wskaźnik do wartości IntPtr.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );  
```  
  
### <a name="parameters"></a>Parametry  
 Wartość1  
 Wskaźnik do dojścia lub IntPtr.  
  
 Wartość2  
 32-bitowa liczba całkowita, która może zostać przekonwertowany na element IntPtr.  
  
 Wartość3  
 Element IntPtr.  
  
### <a name="return-value"></a>Wartość zwracana  
 Operatory pierwszego i drugiego zwracać element IntPtr. Trzeci operator zwraca wskaźnik do reprezentowaną przez bieżące IntPtr.  
  


## <a name="toint32"></a> IntPtr::ToInt32 — metoda
Konwertuje wartość bieżącą IntPtr 32-bitową liczbę całkowitą.  
  
### <a name="syntax"></a>Składnia  
  
```cpp  
int32 IntPtr::ToInt32();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 32-bitową liczbę całkowitą.  
  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)