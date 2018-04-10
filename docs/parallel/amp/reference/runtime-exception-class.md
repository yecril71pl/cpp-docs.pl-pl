---
title: runtime_exception — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- runtime_exception
- AMPRT/runtime_exception
- AMPRT/Concurrency::runtime_exception
- AMPRT/Concurrency::runtime_exception::get_error_code
dev_langs:
- C++
helpviewer_keywords:
- runtime_exception class
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 678f0a93577a6e30afbc5e0c6d83aca6b6a7bedc
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="runtimeexception-class"></a>runtime_exception — Klasa
Typ podstawowy dla wyjątków w bibliotece C++ Accelerated ogromną równoległości (AMP).  
  
### <a name="syntax"></a>Składnia  
  
```  
class runtime_exception : public std::exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[runtime_exception Constructor](#ctor)|Inicjuje nowe wystąpienie klasy `runtime_exception` klasy.|  
|[~runtime_exception Destructor](#dtor)|Niszczy `runtime_exception` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_error_code](#runtime_exception__get_error_code)|Zwraca kod błędu, który spowodował wyjątek.|  

  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator=](#operator_eq)|Kopiuje zawartość określonego `runtime_exception` obiektu do tego.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  

## <a name="runtime_exception__ctor"></a>  runtime_exception — Konstruktor  
Inicjuje nowe wystąpienie klasy.  
  
### <a name="syntax"></a>Składnia  
  
```  
runtime_exception(  
    const char * _Message,  
    HRESULT _Hresult ) throw();  
  
explicit runtime_exception(  
    HRESULT _Hresult ) throw();  
  
runtime_exception(  
    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Opis błędu, który spowodował wyjątek.  
  
 `_Hresult`  
 HRESULT błędu, który spowodował wyjątek.  
  
 `_Other`  
 `runtime_exception` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `runtime_exception` Obiektu.  

## <a name="dtor"></a>  ~ runtime_exception — destruktor  
Niszczy obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
virtual ~runtime_exception() throw();  
```  
  
## <a name="runtime_exception__get_error_code"></a>  get_error_code   
Zwraca kod błędu, który spowodował wyjątek.  
  
### <a name="syntax"></a>Składnia  
  
```  
HRESULT get_error_code() const throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 HRESULT błędu, który spowodował wyjątek.  
  
## <a name="runtime_exception__operator_eq"></a>  operator =   
  Kopiuje zawartość określonego `runtime_exception` obiektu do tego.  
  
### <a name="syntax"></a>Składnia  
  
```  
runtime_exception & operator= (    const runtime_exception & _Other ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `runtime_exception` Obiektu do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do tego `runtime_exception` obiektu.  
  

  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
