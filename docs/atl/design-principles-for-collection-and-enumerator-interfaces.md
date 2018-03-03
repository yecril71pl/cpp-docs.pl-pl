---
title: "Projektowanie kolekcji i interfejsy modułu wyliczającego (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8709274e1b95816dee01b4457993521dde5d5213
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Zasady projektowania dla kolekcji i interfejsy modułu wyliczającego
Istnieją zasady projektowania za każdego typu interfejsu:  
  
-   Udostępnia interfejs kolekcji *losowe* dostęp do *pojedynczego* elementu w kolekcji za pomocą **elementu** metody umożliwia klientom odnajdowanie są liczbę elementów w kolekcji za pomocą **liczba** właściwości, oraz często zezwala klientom na dodawanie i usuwanie elementów.  
  
-   Udostępnia interfejs modułu wyliczającego *serial* dostęp do *wiele* elementów w kolekcji, jego nie zezwala na klienta dowiedzieć się, ile elementów znajdują się w kolekcji (do czasu modułu wyliczającego zatrzymuje zwracanie elementy), a nie zapewnia żadnych sposób dodawania lub usuwania elementów.  
  
 Każdego typu interfejsu pełni rolę innego udzielając dostęp do elementów w kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

