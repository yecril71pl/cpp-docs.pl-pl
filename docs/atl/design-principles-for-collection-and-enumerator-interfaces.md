---
title: Projektowanie interfejsów kolekcji i wyliczeń (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- enumerator interfaces
- collection interfaces
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
ms.openlocfilehash: f40c86d3bc8d9b4e4c752fe6657f6a5a14f19e0c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269939"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Zasady projektowania interfejsów kolekcji i wyliczeń

Istnieją zasady dotyczące projektowania każdego typu interfejsu:

- Udostępnia interfejs kolekcji *losowych* dostęp do *pojedynczego* elementu w kolekcji za pomocą `Item` metody umożliwia klientom odnajdywanie, ile elementów znajdują się w kolekcji za pomocą `Count` właściwości i często umożliwia klientom dodawanie i usuwanie elementów.

- Udostępnia interfejs modułu wyliczającego *serial* dostęp do *wielu* elementów w kolekcji, nie zezwalał na klienta dowiedzieć się, ile elementów są w kolekcji (aż do modułu wyliczającego zatrzymuje, zwracając elementy), a nie udostępnia żadnym dodawania lub usuwania elementów.

Każdy typ interfejsu odgrywa inną rolę w zapewnieniu dostępu do elementów w kolekcji.

## <a name="see-also"></a>Zobacz także

[Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)
