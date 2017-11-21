---
title: "accelerator_view_removed — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs: C++
helpviewer_keywords: AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ca0f97432c92b821a6fef941e1a3d9dc6d542de9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed — klasa
Wyjątek zgłaszany, gdy podstawowy wywołań programu DirectX zakończy się niepowodzeniem z powodu limitu czasu Windows mechanizm wykrywania i odzyskiwania.  
  
## <a name="syntax"></a>Składnia  
  
```  
class accelerator_view_removed : public runtime_exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[accelerator_view_removed — Konstruktor](#ctor)|Inicjuje nowe wystąpienie klasy `accelerator_view_removed` klasy.|  

### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get_view_removed_reason](#get_view_removed_reason)|Zwraca kod błędu HRESULT wskazujący przyczynę `accelerator_view` usuwania obiektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** amprt.h  
  
 **Namespace:** współbieżności  

## <a name="ctor"></a>accelerator_view_removed — 

Inicjuje nowe wystąpienie klasy [accelerator_view_removed —](accelerator-view-removed-class.md) klasy.  
  
### <a name="syntax"></a>Składnia  
  
```  
explicit accelerator_view_removed(  
    const char * _Message,  
    HRESULT _View_removed_reason ) throw();  
  
explicit accelerator_view_removed(  
    HRESULT _View_removed_reason ) throw();  
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Opis błędu.  
  
 `_View_removed_reason`  
 Kod błędu HRESULT wskazujący przyczynę usunięcie `accelerator_view` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe wystąpienie klasy accelerator_view_removed —.  
  
## <a name="get_view_removed_reason_method"></a>get_view_removed_reason 

Zwraca kod błędu HRESULT wskazujący przyczynę `accelerator_view` usuwania obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
HRESULT get_view_removed_reason() const throw();  
```  
  
 
## <a name="see-also"></a>Zobacz też  
 [Namespace współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
