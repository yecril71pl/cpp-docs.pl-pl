---
title: 'Kontenery: implementowanie kontenera'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 89bb8b483dba6e635eef5d9857bb558eca8e8fec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546708"
---
# <a name="containers-implementing-a-container"></a>Kontenery: implementowanie kontenera

Ten artykuł zawiera podsumowanie sposób stosowania kontenera i punktów do innych artykułów, które zawierają bardziej szczegółowe objaśnienia dotyczące wdrożenia kontenerów. Zawiera również listę niektórych funkcji opcjonalnych OLE, który chcesz wdrożyć i artykuły opisujące te funkcje.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Aby przygotować klasy pochodnej CWinApp

1. Zainicjuj biblioteki OLE, wywołując `AfxOleInit` w `InitInstance` funkcja elementu członkowskiego.

1. Wywołaj `CDocTemplate::SetContainerInfo` w `InitInstance` można przypisać w menu i akcelerator zasoby używane podczas osadzonego elementu jest aktywowany w miejscu. Aby uzyskać więcej informacji na ten temat, zobacz [aktywacji](../mfc/activation-cpp.md).

Te funkcje są dostarczane dla Ciebie automatycznie podczas tworzenia aplikacji kontenera za pomocą Kreatora aplikacji MFC. Zobacz [tworzenie programu MFC EXE](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Aby przygotować klasy widoku

1. Zachowaj śledzić wybranych elementów poprzez utrzymywanie wskaźnik lub listy wskaźników, jeżeli obsługuje wiele zaznaczeń do wybranych elementów. Twoje `OnDraw` funkcja musi narysuj wszystkie elementy OLE.

1. Zastąp `IsSelected` do sprawdzenia, czy element przekazany do niego jest aktualnie wybrany.

1. Implementowanie `OnInsertObject` obsługi wiadomości, aby wyświetlić **Wstawianie obiektu** okno dialogowe.

1. Implementowanie `OnSetFocus` wiadomości program obsługi, aby przenieść fokus z widoku active OLE w miejscu osadzonego elementu.

1. Implementowanie `OnSize` obsługi wiadomości, aby informować OLE osadzonych elementów należy zmienić jego prostokąt, aby odzwierciedlić zmiany rozmiaru jej widok zawierający.

Ponieważ implementacji tych funkcji różni się znacznie z jednej aplikacji do następnego Kreatora aplikacji dostarcza podstawową implementację. Prawdopodobnie trzeba będzie dostosować te funkcje można pobrać aplikację, aby działać prawidłowo. Aby na przykład, zobacz [kontenera](../visual-cpp-samples.md) próbki.

#### <a name="to-handle-embedded-and-linked-items"></a>Aby obsłużyć elementy osadzone i połączone

1. Wyprowadzić klasę z [COleClientItem](../mfc/reference/coleclientitem-class.md). Obiekty tej klasy reprezentują elementy, które zostały osadzone w lub połączone z dokumentu OLE.

1. Zastąp `OnChange`, `OnChangeItemPosition`, i `OnGetItemPosition`. Te funkcje uchwyt zmiany rozmiaru, pozycjonowanie i modyfikowania elementy osadzone i połączone.

Kreator aplikacji, z której pochodzą klasę dla Ciebie, ale prawdopodobnie trzeba będzie zastąpić `OnChange` i inne funkcje wyświetlane z nim w kroku 2 w poprzedniej procedurze. Implementacje szkielet muszą zostać dostosowane dla większości aplikacji, ponieważ te funkcje są implementowane w inny sposób z jednej aplikacji do następnego. Przykłady tego, zobacz przykłady MFC [DRAWCLI](../visual-cpp-samples.md) i [kontenera](../visual-cpp-samples.md).

Liczba elementów należy dodać do aplikacji kontenera menu struktury do obsługi OLE. Aby uzyskać więcej informacji na ten temat, zobacz [menu i zasoby: dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).

Można również obsługuje niektóre z następujących funkcji w aplikacji kontenera:

- Aktywacja w miejscu podczas edytowania osadzonego elementu.

   Aby uzyskać więcej informacji, zobacz [aktywacji](../mfc/activation-cpp.md).

- Tworzenie elementu OLE elementów, przeciągając i upuszczając zaznaczenia z aplikacji serwera.

   Aby uzyskać więcej informacji, zobacz [przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md).

- Zawiera łącza do osadzonych obiektów lub kombinacji aplikacje kontenera/serwera.

   Aby uzyskać więcej informacji, zobacz [kontenery: funkcje zaawansowane](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Zobacz też

[Kontenery](../mfc/containers.md)<br/>
[Kontenery: elementy klienckie](../mfc/containers-client-items.md)

