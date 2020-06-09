---
title: 'Kontenery: implementowanie kontenera'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 0ba8d4aea6b69fdbfeedfba59449d0d30433eb94
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623227"
---
# <a name="containers-implementing-a-container"></a>Kontenery: implementowanie kontenera

Ten artykuł podsumowuje procedurę wdrażania kontenera i wskazuje na inne artykuły, które zawierają bardziej szczegółowe wyjaśnienia dotyczące implementowania kontenerów. Zawiera on również niektóre opcjonalne funkcje OLE, które warto zaimplementować i artykuły opisujące te funkcje.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>Aby przygotować klasę pochodną CWinApp

1. Zainicjuj biblioteki OLE, wywołując `AfxOleInit` w `InitInstance` funkcji członkowskiej.

1. Wywołaj metodę `CDocTemplate::SetContainerInfo` `InitInstance` , aby przypisać menu i zasoby akceleratora, które są używane, gdy element osadzony jest aktywowany w miejscu. Aby uzyskać więcej informacji na temat tego tematu, zobacz [Aktywacja](activation-cpp.md).

Te funkcje są udostępniane automatycznie w przypadku tworzenia aplikacji kontenera za pomocą Kreatora aplikacji MFC. Zobacz [Tworzenie programu MFC exe](reference/mfc-application-wizard.md).

#### <a name="to-prepare-your-view-class"></a>Aby przygotować klasę widoku

1. Śledź wybrane elementy, utrzymując wskaźnik lub listę wskaźników w przypadku obsługi wielu zaznaczeń do wybranych elementów. `OnDraw`Funkcja musi rysować wszystkie elementy OLE.

1. Przesłoń, `IsSelected` Aby sprawdzić, czy element przeszedł do niego jest obecnie zaznaczony.

1. Zaimplementuj `OnInsertObject` procedurę obsługi komunikatów, aby wyświetlić okno dialogowe **Wstawianie obiektu** .

1. Zaimplementuj `OnSetFocus` procedurę obsługi komunikatów, aby przenieść fokus z widoku do aktywnego elementu OLE osadzonego w miejscu.

1. Zaimplementuj `OnSize` procedurę obsługi komunikatów, aby poinformować element osadzony OLE o konieczności zmiany jego prostokąta w celu odzwierciedlenia zmiany rozmiaru widoku zawierającego.

Ponieważ implementacja tych funkcji różni się znacznie od jednej aplikacji do następnej, Kreator aplikacji udostępnia tylko podstawową implementację. Prawdopodobnie trzeba będzie dostosować te funkcje, aby aplikacja działała prawidłowo. Przykład tego przykładu znajduje się w sekcji [Container](../overview/visual-cpp-samples.md) przykład.

#### <a name="to-handle-embedded-and-linked-items"></a>Aby obsłużyć osadzone i połączone elementy

1. Utwórz klasę z [COleClientItem](reference/coleclientitem-class.md). Obiekty tej klasy reprezentują elementy, które zostały osadzone w lub połączone z dokumentem OLE.

1. Przesłoń `OnChange` , `OnChangeItemPosition` , i `OnGetItemPosition` . Te funkcje obsługują rozmiary, pozycjonowanie i modyfikowanie osadzonych i połączonych elementów.

Kreator aplikacji będzie dziedziczyć klasę, ale prawdopodobnie trzeba będzie przesłonić `OnChange` i inne funkcje wymienione w kroku 2 w poprzedniej procedurze. Implementacje szkieletowe muszą być dostosowane do większości aplikacji, ponieważ te funkcje są implementowane inaczej od jednej aplikacji do następnej. Aby zapoznać się z przykładami, zobacz MFC Samples [DRAWCLI](../overview/visual-cpp-samples.md) i [Container](../overview/visual-cpp-samples.md).

Aby zapewnić obsługę OLE, należy dodać wiele elementów do struktury menu aplikacji kontenera. Aby uzyskać więcej informacji na ten temat, zobacz [menu i zasoby: Dodatki do kontenera](menus-and-resources-container-additions.md).

Może być również konieczne obsłudze niektórych z następujących funkcji w aplikacji kontenera:

- Aktywacja w miejscu podczas edytowania elementu osadzonego.

   Aby uzyskać więcej informacji, zobacz [Aktywacja](activation-cpp.md).

- Tworzenie elementów OLE przez przeciąganie i upuszczanie zaznaczenia z aplikacji serwera.

   Aby uzyskać więcej informacji, zobacz [OLE przeciąganie i upuszczanie](drag-and-drop-ole.md).

- Linki do obiektów osadzonych lub kombinacji aplikacji kontenera/serwera.

   Aby uzyskać więcej informacji, zobacz [Containers: Advanced Features](containers-advanced-features.md).

## <a name="see-also"></a>Zobacz też

[Containers](containers.md)<br/>
[Kontenery: elementy klienckie](containers-client-items.md)
