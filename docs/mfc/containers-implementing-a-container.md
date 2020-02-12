---
title: 'Kontenery: implementowanie kontenera'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: ed95324b8df978a6ab2f7582c0ddf626a45e7fe1
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127923"
---
# <a name="containers-implementing-a-container"></a>Kontenery: implementowanie kontenera

Ten artykuł podsumowuje procedurę wdrażania kontenera i wskazuje na inne artykuły, które zawierają bardziej szczegółowe wyjaśnienia dotyczące implementowania kontenerów. Zawiera on również niektóre opcjonalne funkcje OLE, które warto zaimplementować i artykuły opisujące te funkcje.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Aby przygotować klasę pochodną CWinApp

1. Zainicjuj biblioteki OLE, wywołując `AfxOleInit` w funkcji członkowskiej `InitInstance`.

1. Wywołaj `CDocTemplate::SetContainerInfo` w `InitInstance`, aby przypisać menu i zasoby akceleratora, które są używane, gdy element osadzony jest aktywowany w miejscu. Aby uzyskać więcej informacji na temat tego tematu, zobacz [Aktywacja](../mfc/activation-cpp.md).

Te funkcje są udostępniane automatycznie w przypadku tworzenia aplikacji kontenera za pomocą Kreatora aplikacji MFC. Zobacz [Tworzenie programu MFC exe](../mfc/reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Aby przygotować klasę widoku

1. Śledź wybrane elementy, utrzymując wskaźnik lub listę wskaźników w przypadku obsługi wielu zaznaczeń do wybranych elementów. Funkcja `OnDraw` musi rysować wszystkie elementy OLE.

1. Zastąp `IsSelected`, aby sprawdzić, czy element, do którego został przeniesiony, jest obecnie zaznaczony.

1. Zaimplementuj procedurę obsługi komunikatów `OnInsertObject`, aby wyświetlić okno dialogowe **Wstawianie obiektu** .

1. Zaimplementuj procedurę obsługi komunikatów `OnSetFocus`, aby przenieść fokus z widoku do aktywnego elementu OLE osadzonego w miejscu.

1. Zaimplementuj procedurę obsługi komunikatów `OnSize`, aby poinformować element osadzony OLE o konieczności zmiany jego prostokąta w celu odzwierciedlenia zmiany rozmiaru widoku zawierającego.

Ponieważ implementacja tych funkcji różni się znacznie od jednej aplikacji do następnej, Kreator aplikacji udostępnia tylko podstawową implementację. Prawdopodobnie trzeba będzie dostosować te funkcje, aby aplikacja działała prawidłowo. Przykład tego przykładu znajduje się w sekcji [Container](../overview/visual-cpp-samples.md) przykład.

#### <a name="to-handle-embedded-and-linked-items"></a>Aby obsłużyć osadzone i połączone elementy

1. Utwórz klasę z [COleClientItem](../mfc/reference/coleclientitem-class.md). Obiekty tej klasy reprezentują elementy, które zostały osadzone w lub połączone z dokumentem OLE.

1. Przesłoń `OnChange`, `OnChangeItemPosition`i `OnGetItemPosition`. Te funkcje obsługują rozmiary, pozycjonowanie i modyfikowanie osadzonych i połączonych elementów.

Kreator aplikacji będzie dziedziczyć klasę, ale prawdopodobnie trzeba będzie przesłonić `OnChange` i inne funkcje wymienione w kroku 2 w poprzedniej procedurze. Implementacje szkieletowe muszą być dostosowane do większości aplikacji, ponieważ te funkcje są implementowane inaczej od jednej aplikacji do następnej. Aby zapoznać się z przykładami, zobacz MFC Samples [DRAWCLI](../overview/visual-cpp-samples.md) i [Container](../overview/visual-cpp-samples.md).

Aby zapewnić obsługę OLE, należy dodać wiele elementów do struktury menu aplikacji kontenera. Aby uzyskać więcej informacji na ten temat, zobacz [menu i zasoby: Dodatki do kontenera](../mfc/menus-and-resources-container-additions.md).

Może być również konieczne obsłudze niektórych z następujących funkcji w aplikacji kontenera:

- Aktywacja w miejscu podczas edytowania elementu osadzonego.

   Aby uzyskać więcej informacji, zobacz [Aktywacja](../mfc/activation-cpp.md).

- Tworzenie elementów OLE przez przeciąganie i upuszczanie zaznaczenia z aplikacji serwera.

   Aby uzyskać więcej informacji, zobacz [OLE przeciąganie i upuszczanie](../mfc/drag-and-drop-ole.md).

- Linki do obiektów osadzonych lub kombinacji aplikacji kontenera/serwera.

   Aby uzyskać więcej informacji, zobacz [Containers: Advanced Features](../mfc/containers-advanced-features.md).

## <a name="see-also"></a>Zobacz też

[Kontenery](../mfc/containers.md)<br/>
[Kontenery: elementy klienckie](../mfc/containers-client-items.md)
