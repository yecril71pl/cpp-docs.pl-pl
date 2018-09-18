---
title: context_unblock_unbalanced — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs:
- C++
helpviewer_keywords:
- context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54911e3e9c696cd2a390dc2f5b42e3917b08014f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037479"
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced — Klasa
Ta klasa opisuje wyjątek generowany, gdy wywołuje w celu `Block` i `Unblock` metody `Context` obiektu nie są prawidłowo skojarzone.  
  
## <a name="syntax"></a>Składnia  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[context_unblock_unbalanced](#ctor)|Przeciążone. Konstruuje `context_unblock_unbalanced` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołania `Block` i `Unblock` metody `Context` obiektu muszą zawsze być prawidłowo skojarzone. Współbieżność środowiska umożliwia wykonywanie operacji do wykonania w obu kolejności. Na przykład, wywołanie `Block` może następować po wywołaniu `Unblock`, lub na odwrót. Ten wyjątek będzie zgłaszany, jeśli na przykład dwa wywołania `Unblock` metody zostały wprowadzone w wierszu, a na `Context` obiektu, który nie został zablokowany.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a> context_unblock_unbalanced — 

 Konstruuje `context_unblock_unbalanced` obiektu.  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>Parametry  
*_Message*<br/>
Opisowy komunikat dotyczący błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
