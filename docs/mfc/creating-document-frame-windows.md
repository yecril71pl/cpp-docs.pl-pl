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
ms.openlocfilehash: 66a951994a75cbd99debeb2c6511739411cdd470
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174032"
---
# <a name="creating-document-frame-windows"></a>Tworzenie okien ramowych dokumentu

[Tworzenie dokumentu/widoku](../mfc/document-view-creation.md) pokazano sposób, w jaki [CDocTemplate](../mfc/reference/cdoctemplate-class.md) obiektu organizuje tworzenia okna ramki dokumentu i widok oraz łączenie ich wszystkich. Trzy [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) argumenty `CDocTemplate` Konstruktor Określ okno ramowe, dokumentów i klasy widoku, które szablon dokumentu, który tworzy się dynamicznie w odpowiedzi na polecenia użytkownika, takie jak nowe polecenie na pliku menu lub nowe okno polecenia menu okna MDI. Szablon dokumentu, który przechowuje te informacje w celu późniejszego użycia podczas tworzenia okna ramki dla widoku i dokumentu.

Dla [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class) mechanizm działają poprawnie, Twoje pochodne klasy okien ramowych musi być zadeklarowany z [DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate) makra. Jest to spowodowane ramach potrzebne do utworzenia dokumentu przy użyciu mechanizmu dynamiczna konstrukcja klasy okna ramowe `CObject`.

Gdy użytkownik wybierze polecenie, które tworzy dokument, struktura wywołuje od szablonu dokumentu, aby utworzyć obiekt dokumentu, jej widok i w oknie ramki, w którym będą wyświetlane w widoku. Podczas tworzenia okna ramki dokumentu, szablon dokumentu, który tworzy obiekt klasy odpowiedniego — klasą pochodną [CFrameWnd](../mfc/reference/cframewnd-class.md) do aplikacji interfejsu SDI lub na podstawie [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) dla MDI aplikacja. Struktura następnie wywołuje obiekt okno ramowe [loadframe —](../mfc/reference/cframewnd-class.md#loadframe) funkcja elementu członkowskiego, aby uzyskać informacje o tworzeniu z zasobami i można utworzyć okna Windows. Struktura dołącza uchwyt okna do obiektu ramki okna. Następnie tworzy widok jako okna podrzędnego okna ramki dokumentu.

Należy zachować ostrożność podczas podejmowania decyzji [kiedy inicjować](../mfc/when-to-initialize-cwnd-objects.md) swoje `CWnd`-pochodnych obiektu.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Wyprowadzanie klasy z obiektu CObject (jego mechanizm dynamiczne tworzenie)](../mfc/deriving-a-class-from-cobject.md)

- [Tworzenie dokumentu/widoku (szablonów i tworzenie okien ramowych)](../mfc/document-view-creation.md)

- [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>Zobacz także

[Używanie okien ramowych](../mfc/using-frame-windows.md)
