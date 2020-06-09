---
title: Tworzenie okien ramowych dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], creating
- document templates [MFC], and document frame windows
- windows [MFC], creating
- runtime, class information
- run-time class [MFC], and document frame window creation
- document frame windows [MFC], creating
- MFC, frame windows
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
ms.openlocfilehash: e15a2a6bc016bf23bc0decf529b4c3ffeecc3a4c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621949"
---
# <a name="creating-document-frame-windows"></a>Tworzenie okien ramowych dokumentu

[Tworzenie dokumentu/widoku](document-view-creation.md) pokazuje, jak obiekt [CDocTemplate](reference/cdoctemplate-class.md) organizuje tworzenie okna ramki, dokumentu i widoku oraz łączenie ich ze sobą. Trzy argumenty [CRuntimeClass](reference/cruntimeclass-structure.md) do `CDocTemplate` konstruktora określają okno ramki, dokument i klasy widoku, które szablon dokumentu tworzy dynamicznie w odpowiedzi na polecenia użytkownika, takie jak nowe polecenie w menu plik lub polecenie nowe okno w menu w oknie MDI. Szablon dokumentu przechowuje te informacje do późniejszego użycia podczas tworzenia okna ramowego dla widoku i dokumentu.

Aby mechanizm [RUNTIME_CLASS](reference/run-time-object-model-services.md#runtime_class) działał poprawnie, pochodne klasy okien ramowych muszą być zadeklarowane za pomocą makra [DECLARE_DYNCREATE](reference/run-time-object-model-services.md#declare_dyncreate) . Wynika to z faktu, że struktura musi utworzyć okna z ramkami dokumentu przy użyciu mechanizmu konstruowania dynamicznego klasy `CObject` .

Gdy użytkownik wybierze polecenie, które tworzy dokument, struktura wywołuje szablon dokumentu, aby utworzyć obiekt dokumentu, jego widok i okno ramki, w których zostanie wyświetlony widok. Po utworzeniu okna ramki dokumentu szablon dokumentu tworzy obiekt odpowiedniej klasy — klasy pochodnej [obiektu CFrameWnd](reference/cframewnd-class.md) dla aplikacji SDI lub [CMDICHILDWND](reference/cmdichildwnd-class.md) dla aplikacji MDI. Struktura następnie wywołuje funkcję członkowską [LoadFrame](reference/cframewnd-class.md#loadframe) obiektu ramki okna, aby uzyskać informacje o tworzeniu z zasobów i utworzyć okno systemu Windows. Struktura dołącza uchwyt okna do obiektu okna ramki. Następnie tworzy widok jako okno podrzędne okna ramki dokumentu.

Należy zachować ostrożność przy podejmowaniu decyzji [o zainicjowaniu](when-to-initialize-cwnd-objects.md) `CWnd` obiektu pochodnego.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Wyprowadzanie klasy z CObject (jej mechanizmu tworzenia dynamicznego)](deriving-a-class-from-cobject.md)

- [Tworzenie dokumentu/widoku (szablony i tworzenie okien ramowych)](document-view-creation.md)

- [Niszczenie okien ramowych](destroying-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](using-frame-windows.md)
