---
title: Błąd PRJ0030 kompilacji projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf1c9137f8c4ed0d80955eef38b07ea86204a5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317661"
---
# <a name="project-build-error-prj0030"></a>Błąd PRJ0030 kompilacji projektu
Błąd rozwinięcie makra. Ocena rekursja przekroczyła 32 poziomy dla $(makro).  
  
 Ten błąd jest spowodowany przez rekursji w makrach. Na przykład jeśli ustawisz **katalog pośredni** właściwości (zobacz [ogólna strona właściwości (projekt)](../../ide/general-property-page-project.md)) do $(intdir —), konieczne będzie rekursji.  
  
 Aby rozwiązać ten problem, nie definiują właściwości pod względem makra, które są one używane do definiowania lub makra.