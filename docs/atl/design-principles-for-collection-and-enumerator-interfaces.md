---
title: Projektowanie kolekcji i interfejsy modułu wyliczającego (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05649cce0e80af6f54327545cef7b663d69babf9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Zasady projektowania dla kolekcji i interfejsy modułu wyliczającego
Istnieją zasady projektowania za każdego typu interfejsu:  
  
-   Udostępnia interfejs kolekcji *losowe* dostęp do *pojedynczego* elementu w kolekcji za pomocą **elementu** metody umożliwia klientom odnajdowanie są liczbę elementów w kolekcji za pomocą **liczba** właściwości, oraz często zezwala klientom na dodawanie i usuwanie elementów.  
  
-   Udostępnia interfejs modułu wyliczającego *serial* dostęp do *wiele* elementów w kolekcji, jego nie zezwala na klienta dowiedzieć się, ile elementów znajdują się w kolekcji (do czasu modułu wyliczającego zatrzymuje zwracanie elementy), a nie zapewnia żadnych sposób dodawania lub usuwania elementów.  
  
 Każdego typu interfejsu pełni rolę innego udzielając dostęp do elementów w kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

