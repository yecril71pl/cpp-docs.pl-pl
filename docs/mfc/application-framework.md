---
title: Struktura aplikacji
ms.date: 11/04/2016
helpviewer_keywords:
- application framework [MFC], building applications
- applications [MFC]
- application framework [MFC]
ms.assetid: 912684e6-4418-49dc-9877-a4cd19d69d20
ms.openlocfilehash: b55635de322274ab02372251976d4ebb9511ade5
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446521"
---
# <a name="application-framework"></a>Struktura aplikacji

Rdzeń biblioteki Microsoft Foundation Class (MFC) jest hermetyzacją dużej części interfejsu API systemu Windows w C++ postaci. Klasy bibliotek reprezentują okna, okna dialogowe, konteksty urządzeń, typowe obiekty GDI, takie jak pędzle i pióra, kontrolki i inne standardowe elementy systemu Windows. Klasy te zapewniają wygodny C++ interfejs funkcji składowej dla struktur w systemie Windows, które hermetyzują. Aby uzyskać więcej informacji na temat korzystania z tych klas, zobacz [temat obiekty okna](../mfc/window-objects.md).

Jednak biblioteka MFC udostępnia również warstwę dodatkowych funkcji aplikacji wbudowanych w C++ HERMETYZACJĘ interfejsu API systemu Windows. Ta warstwa jest działającą platformą aplikacji dla systemu Windows, która zapewnia większość typowych interfejsów użytkownika oczekiwanych przez programy dla systemu Windows, w tym paski narzędzi, paski stanu, drukowanie, Podgląd wydruku, obsługa bazy danych i obsługę ActiveX. [Korzystanie z klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md) objaśnia szczegółowo strukturę.

## <a name="see-also"></a>Zobacz też

[Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
