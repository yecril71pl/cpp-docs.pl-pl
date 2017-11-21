---
title: Klasa platform::ChangedStateException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
dev_langs: C++
helpviewer_keywords: Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: c567a49f3365f4c18c5acc174cdac09d0408f022
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="platformchangedstateexception-class"></a>Klasa platform::ChangedStateException
Element zgłaszany, gdy stan wewnętrzny obiektu uległ zmianie, a tym samym unieważnienie wyniki metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="remarks"></a>Uwagi  
 Przykładem, w którym ten wyjątek jest w przypadku metody iterator kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, unieważnia wyniki metody.  
  
 Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.  
  
### <a name="requirements"></a>Wymagania  
 **Minimalna obsługiwana klienta:** systemu Windows 8  
  
 **Minimalna obsługiwana serwera:** systemu Windows Server 2012  
  
 **Namespace:** platformy  
  
 **Metadane:** platform.winmd  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa platform::COMException](../cppcx/platform-comexception-class.md)