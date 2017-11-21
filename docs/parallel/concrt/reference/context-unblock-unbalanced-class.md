---
title: "context_unblock_unbalanced — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced
- CONCRT/concurrency::context_unblock_unbalanced::context_unblock_unbalanced
dev_langs: C++
helpviewer_keywords: context_unblock_unbalanced class
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 45121b3dba14e5672333debf364f5aea2e3e3cd5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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
|[context_unblock_unbalanced —](#ctor)|Przeciążone. Konstruuje `context_unblock_unbalanced` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołuje się `Block` i `Unblock` metody `Context` obiektu muszą zawsze prawidłowo łączyć. Współbieżność środowiska wykonawczego zezwala na wykonywanie operacji w każdej kolejności. Na przykład wywołanie `Block` może występować przez wywołanie do `Unblock`, lub na odwrót. Ten wyjątek może zostać zgłoszony, jeśli na przykład dwa wywołań `Unblock` metodę wprowadzono w wierszu na `Context` obiektu, który nie został zablokowany.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
 **Namespace:** współbieżności  
  
##  <a name="ctor"></a>context_unblock_unbalanced — 

 Konstruuje `context_unblock_unbalanced` obiektu.  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>Parametry  
 `_Message`  
 Komunikat opisowy błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność Namespace](concurrency-namespace.md)
