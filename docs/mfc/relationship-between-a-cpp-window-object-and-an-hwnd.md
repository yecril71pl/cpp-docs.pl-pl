---
title: Relacja między obiektem okna języka C++ a właściwością HWND | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- HWND
dev_langs:
- C++
helpviewer_keywords:
- Windows window [MFC]
- window objects [MFC], HWND and
- HWND [MFC]
- CWnd class [MFC], HWND
- HWND, window objects [MFC]
ms.assetid: f2e76340-6691-4ee6-9424-0345634a9469
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 844f62b110f54ba3e2c8909a78d58c9f2c01dcac
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392817"
---
# <a name="relationship-between-a-c-window-object-and-an-hwnd"></a>Relacja między obiektem okna języka C++ a właściwością HWND

Okno *obiektu* jest obiektem C++ `CWnd` klasy (lub klasę pochodną) tworzący bezpośrednio w programie. Ona pochodzi i znajduje się w odpowiedź na wywołania Konstruktor i destruktor dla Twojego programu. Windows *okna*, z drugiej strony jest nieprzezroczysta dojścia do wewnętrznej struktury danych Windows, która odnosi się do okna i wykorzystuje zasoby systemowe, jeśli jest obecny. Okno Windows jest identyfikowany przez "uchwyt okna" (`HWND`) i jest tworzona po `CWnd` obiekt jest tworzony przez wywołanie `Create` funkcji składowej klasy typu `CWnd`. Okna może zostać zniszczone, przez wywołanie programu lub akcji przez użytkownika. Uchwyt okna jest przechowywany w obiekcie okna *m_hWnd* zmiennej składowej. Na poniższej ilustracji przedstawiono relację między obiektem okna języka C++ i okno Windows. Tworzenie okien zostało omówione w [tworzenia Windows](../mfc/creating-windows.md). Niszczenie okien zostało omówione w [niszczenie obiektów okien](../mfc/destroying-window-objects.md).

![CWnd obiekt okna i okna wynikowe](../mfc/media/vc37fj1.gif "vc37fj1") obiekt okna i okna Windows

## <a name="see-also"></a>Zobacz też

[Obiekty okna](../mfc/window-objects.md)

