---
title: "Dostęp do biblioteki typu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.macros
dev_langs: C++
helpviewer_keywords: type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bbc5ceabe60d7ee15d85495bb1a431955a589849
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-library-access"></a>Dostęp do biblioteki typów
Biblioteki typów uwidacznia interfejsów kontrolkę OLE do innych aplikacji obsługujących OLE. Każda kontrolka OLE musi mieć biblioteki typów, jeśli jeden lub więcej interfejsów mają być widoczne.  
  
 Zezwalaj na następujące makra formantu OLE w celu zapewnienia dostępu do jego własnej biblioteki typów:  
  
### <a name="type-library-access"></a>Dostęp do biblioteki typów  
  
|||  
|-|-|  
|[DECLARE_OLETYPELIB —](#declare_oletypelib)|Deklaruje `GetTypeLib` funkcji członkowskiej formantów OLE (należy użyć w deklaracji klasy).|  
|[IMPLEMENT_OLETYPELIB —](#implement_oletypelib)|Implementuje `GetTypeLib` funkcji członkowskiej formantów OLE (musi być zastosowany w implementacji klasy).|  
  
##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB —  
 Deklaruje `GetTypeLib` funkcji członkowskiej klasy formantu.  
  
```   
DECLARE_OLETYPELIB(class_name)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu związane z biblioteki typów.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tego makra w pliku nagłówka klasy formantu.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB —  
 Implementuje formantu `GetTypeLib` funkcję elementu członkowskiego.  
  
```   
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)   
```  
  
### <a name="parameters"></a>Parametry  
 *class_name*  
 Nazwa klasy formantu związane z biblioteki typów.  
  
 *tlid*  
 Identyfikator biblioteki typów.  
  
 `wVerMajor`  
 Numer wersji głównej biblioteki typu.  
  
 `wVerMinor`  
 Typ biblioteki podrzędny numer wersji.  
  
### <a name="remarks"></a>Uwagi  
 To makro musi występować w pliku implementacji dla dowolnej klasy formantu, który używa `DECLARE_OLETYPELIB` makra.  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
   
## <a name="see-also"></a>Zobacz też  
 [Makra i funkcje globalne](../../mfc/reference/mfc-macros-and-globals.md)
