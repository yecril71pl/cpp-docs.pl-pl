---
title: "Projektowanie kolekcji i interfejsy modułu wyliczającego (ATL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40aa94226b93a42b14dfd23a64e12fff00e22729
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Zasady projektowania dla kolekcji i interfejsy modułu wyliczającego
Istnieją zasady projektowania za każdego typu interfejsu:  
  
-   Udostępnia interfejs kolekcji *losowe* dostęp do *pojedynczego* elementu w kolekcji za pomocą **elementu** metody umożliwia klientom odnajdowanie są liczbę elementów w kolekcji za pomocą **liczba** właściwości, oraz często zezwala klientom na dodawanie i usuwanie elementów.  
  
-   Udostępnia interfejs modułu wyliczającego *serial* dostęp do *wiele* elementów w kolekcji, jego nie zezwala na klienta dowiedzieć się, ile elementów znajdują się w kolekcji (do czasu modułu wyliczającego zatrzymuje zwracanie elementy), a nie zapewnia żadnych sposób dodawania lub usuwania elementów.  
  
 Każdego typu interfejsu pełni rolę innego udzielając dostęp do elementów w kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

