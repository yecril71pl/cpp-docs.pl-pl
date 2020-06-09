---
title: Struktura aplikacji
ms.date: 11/04/2016
helpviewer_keywords:
- application framework [MFC], building applications
- applications [MFC]
- application framework [MFC]
ms.assetid: 912684e6-4418-49dc-9877-a4cd19d69d20
ms.openlocfilehash: 3d6616380e9461489d208281a34e0b0b4aa2caf0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626019"
---
# <a name="application-framework"></a>Struktura aplikacji

Rdzeń biblioteki Microsoft Foundation Class (MFC) jest hermetyzacją dużej części interfejsu API systemu Windows w postaci języka C++. Klasy bibliotek reprezentują okna, okna dialogowe, konteksty urządzeń, typowe obiekty GDI, takie jak pędzle i pióra, kontrolki i inne standardowe elementy systemu Windows. Klasy te zapewniają wygodny interfejs funkcji składowej C++ do struktur w systemie Windows, które hermetyzują. Aby uzyskać więcej informacji na temat korzystania z tych klas, zobacz [temat obiekty okna](window-objects.md).

Jednak biblioteka MFC udostępnia również warstwę dodatkowych funkcji aplikacji wbudowanych w hermetyzacji języka C++ systemu Windows. Ta warstwa jest działającą platformą aplikacji dla systemu Windows, która zapewnia większość typowych interfejsów użytkownika oczekiwanych przez programy dla systemu Windows, w tym paski narzędzi, paski stanu, drukowanie, Podgląd wydruku, obsługa bazy danych i obsługę ActiveX. [Korzystanie z klas do pisania aplikacji dla systemu Windows](using-the-classes-to-write-applications-for-windows.md) objaśnia szczegółowo strukturę.

## <a name="see-also"></a>Zobacz też

[Ogólne zasady projektowania klas](general-class-design-philosophy.md)
