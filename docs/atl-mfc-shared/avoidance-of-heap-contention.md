---
title: Unikanie rywalizacji stert
ms.date: 11/04/2016
helpviewer_keywords:
- heap contention
ms.assetid: 797129d7-5f8c-4b0e-8974-bb93217e9ab5
ms.openlocfilehash: 45510607a63759aad9444959716bef164eda1492
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743284"
---
# <a name="avoidance-of-heap-contention"></a>Unikanie rywalizacji stert

Domyślny ciąg menedżerowie dostarczonych przez MFC i ATL to proste otoki na szczycie stosu globalnego. Ten globalny sterty jest całkowicie bezpieczna dla wątków, co oznacza, że wiele wątków może alokują i zwalniają pamięć z niego jednocześnie bez uszkodzenia sterty. Aby zapewnić bezpieczeństwo wątków stosu ma serializować dostępu do samego siebie. Zazwyczaj jest to realizowane przy użyciu sekcję krytyczną lub podobny mechanizm blokowania. Zawsze, gdy dwa wątki próby jednocześnie dostęp do sterty, jeden wątek jest zablokowany do momentu zakończenia żądania innego wątku. W przypadku wielu aplikacji taka sytuacja występuje rzadko i wpływ na wydajność mechanizm blokowania sterty jest niewielka. Jednak dla aplikacji, które sterty jest często używany z wielu wątków rywalizacji o blokadę sterty może spowodować aplikacji, aby działała wolniej niż jeśli były jednowątkowe (nawet na maszynach z wielu procesorów).

Aplikacje, które używają [CStringT](../atl-mfc-shared/reference/cstringt-class.md) są szczególnie podatne na rywalizacji stert ponieważ operacje na `CStringT` obiekty często wymagają ponownej alokacji buforu ciągu miejsca.

Jednym ze sposobów zmniejszenia rywalizacji stert między wątkami ma Każdy wątek przydzielić ciągi ze stosu prywatnych, lokalnej wątku. Tak długo, jak ciągi przydzielona z określonego wątku alokatora są używane tylko w tym wątku, alokator nie musi być metodą o bezpiecznych wątkach.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono procedury wątku, który przydziela swój własny prywatny sterty bez nieobsługująca bezpieczeństwa wątków do użycia dla ciągów, w tym wątku:

[!code-cpp[NVC_ATLMFC_Utilities#182](../atl-mfc-shared/codesnippet/cpp/avoidance-of-heap-contention_1.cpp)]

## <a name="comments"></a>Komentarze

Wiele wątków może być uruchomiony przy użyciu tej samej procedury wątku, ale ponieważ każdy wątek ma swój własny sterty nie występuje Rywalizacja między wątkami. Ponadto fakt, że każdy stos nie jest metodą o bezpiecznych wątkach daje wymierne wzrost wydajności, nawet wtedy, gdy tylko jeden wątek jest uruchomiony. Jest to wynikiem sterty nie używa kosztowne operacje blokowane, aby zapewnić ochronę przed równoczesny dostęp.

Dla bardziej skomplikowane procedury wątku może być wygodne przechowywanie wskaźnika do wątku Menedżera ciągów w gnieździe magazynu lokalnego (TLS) wątku. Dzięki temu inne funkcje wywoływane przez procedurę wątku, aby dostęp do Menedżera ciągów dla wątku.

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
