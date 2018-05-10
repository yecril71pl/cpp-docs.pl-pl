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
ms.openlocfilehash: c964701f9a26c655bbb9529a112f036c7c9f0bf5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="contextunblockunbalanced-class"></a>context_unblock_unbalanced — Klasa
Ta klasa opisuje wyjątek zgłoszony podczas wywołania do `Block` i `Unblock` metody `Context` obiektu nie są poprawnie skojarzone.  
  
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
 Wywołuje się `Block` i `Unblock` metody `Context` obiektu muszą zawsze prawidłowo łączyć. Współbieżność środowiska wykonawczego zezwala na wykonywanie operacji w każdej kolejności. Na przykład wywołanie `Block` może występować przez wywołanie do `Unblock`, lub na odwrót. Ten wyjątek może zostać zgłoszony, jeśli na przykład dwa wywołań `Unblock` metodę wprowadzono w wierszu na `Context` obiektu, który nie został zablokowany.  
  
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
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
