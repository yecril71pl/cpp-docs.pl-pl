---
title: Kontenery formantów ActiveX
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620756"
---
# <a name="activex-control-containers"></a>Kontenery formantów ActiveX

Kontener formantów ActiveX jest kontenerem, który w pełni obsługuje kontrolki ActiveX i może zawierać je w swoich własnych oknach lub oknach dialogowych. Kontrolka ActiveX to element oprogramowania wielokrotnego użytku, którego można użyć w wielu projektach programistycznych. Kontrolki umożliwiają użytkownikowi aplikacji dostęp do baz danych, monitorowanie danych i wybór różnych opcji w aplikacjach. Aby uzyskać więcej informacji na temat kontrolek ActiveX, zobacz artykuł [kontrolki ActiveX MFC](mfc-activex-controls.md).

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji, zobacz [kontrolki ActiveX](activex-controls.md).

Kontenery formantów zazwyczaj przyjmują dwa formularze w projekcie:

- Okna dialogowe i okna dialogowe, takie jak widoki formularzy, gdzie Kontrolka ActiveX jest używana gdzieś w oknie dialogowym.

- System Windows w aplikacji, gdzie Kontrolka ActiveX jest używana na pasku narzędzi lub w innej lokalizacji w oknie użytkownika.

Kontener formantów ActiveX współdziała z kontrolką za pośrednictwem uwidocznionych [metod](mfc-activex-controls-methods.md) i [Właściwości](mfc-activex-controls-properties.md). Te metody i właściwości, które mogą być dostępne i modyfikowane przez kontener sterowania, są dostępne za pomocą klasy otoki w projekcie kontenera kontrolek ActiveX. Osadzony formant ActiveX może również współdziałać z kontenerem przez wyzwolenie (wysłanie) [zdarzeń](mfc-activex-controls-events.md) w celu powiadomienia kontenera o wystąpieniu akcji. Kontener sterowania może zdecydować się na działanie tych powiadomień.

Dodatkowe artykuły omawiają kilka tematów, od tworzenia projektu kontenera kontrolek ActiveX do podstawowych problemów implementacji związanych z kontenerami formantów ActiveX skompilowanymi przy użyciu Visual C++:

- [Tworzenie kontenera kontrolek ActiveX MFC](reference/creating-an-mfc-activex-control-container.md)

- [Kontenery dla kontrolek ActiveX](containers-for-activex-controls.md)

- [Kontenery kontrolek ActiveX: ręczne włączanie zawierania kontrolek ActiveX](activex-control-containers-manually-enabling-activex-control-containment.md)

- [Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek](inserting-a-control-into-a-control-container-application.md)

- [Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną składową](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [Kontenery kontrolek ActiveX: obsługa zdarzeń z kontrolki ActiveX](activex-control-containers-handling-events-from-an-activex-control.md)

- [Kontenery kontrolek ActiveX: wyświetlanie i modyfikowanie właściwości kontrolki](activex-control-containers-viewing-and-modifying-control-properties.md)

- [Kontenery kontrolek ActiveX: programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX](programming-activex-controls-in-a-activex-control-container.md)

- [Kontenery kontrolek ActiveX: używanie kontrolek w kontenerze innym niż okno dialogowe](activex-control-containers-using-controls-in-a-non-dialog-container.md)

Aby uzyskać więcej informacji na temat używania kontrolek ActiveX w oknie dialogowym, zobacz tematy [edytora okien dialogowych](../windows/dialog-editor.md) .

Aby zapoznać się z listą artykułów, które objaśniają szczegóły opracowywania formantów ActiveX przy użyciu Visual C++ i klas formantów ActiveX MFC, zobacz [kontrolki ActiveX MFC](mfc-activex-controls.md). Artykuły są pogrupowane według kategorii funkcjonalnych.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
