---
title: Projektowanie interfejsów kolekcji i wyliczeń (ATL) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 8ffe40b583a9dabeb14ce5347de6ae3d14dae724
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751488"
---
# <a name="design-principles-for-collection-and-enumerator-interfaces"></a>Zasady projektowania interfejsów kolekcji i wyliczeń

Istnieją zasady dotyczące projektowania każdego typu interfejsu:

- Udostępnia interfejs kolekcji *losowych* dostęp do *pojedynczego* elementu w kolekcji za pomocą `Item` metody umożliwia klientom odnajdywanie, ile elementów znajdują się w kolekcji za pomocą `Count` właściwości i często umożliwia klientom dodawanie i usuwanie elementów.

- Udostępnia interfejs modułu wyliczającego *serial* dostęp do *wielu* elementów w kolekcji, nie zezwalał na klienta dowiedzieć się, ile elementów są w kolekcji (aż do modułu wyliczającego zatrzymuje, zwracając elementy), a nie udostępnia żadnym dodawania lub usuwania elementów.

Każdy typ interfejsu odgrywa inną rolę w zapewnieniu dostępu do elementów w kolekcji.

## <a name="see-also"></a>Zobacz też

[Kolekcje i wyliczenia](../atl/atl-collections-and-enumerators.md)

