---
title: 'Schowek: kopiowanie i wklejanie danych'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 7f22418b4006bcb9fac1d4430660c8721bc7e903
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437043"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schowek: kopiowanie i wklejanie danych

W tym temacie opisano minimalną pracy, należy wykonać, kopiowanie i wklejanie ze Schowka w aplikacji OLE. Zalecane jest przeczytanie [obiekty danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) tematy przed kontynuowaniem.

Aby można było zaimplementować kopiowanie lub wklejanie, najpierw należy podać funkcje do obsługi opcji kopiowanie, wycinanie i wklejanie w menu Edycja.

##  <a name="_core_copying_or_cutting_data"></a> Kopiowanie lub Cuttinga danych

#### <a name="to-copy-data-to-the-clipboard"></a>Aby skopiować dane do Schowka

1. Określ dane do skopiowania danych natywnych czy jest to element osadzony lub połączony.

   - Jeśli danych jest osadzony lub połączony, uzyskiwanie wskaźnika do `COleClientItem` obiektu, który został wybrany.

   - Jeśli dane znajdują się w natywnej aplikacji jest serwerem, utworzyć nowy obiekt pochodną `COleServerItem` zawierającą wybrane dane. W przeciwnym razie utwórz `COleDataSource` obiektu danych.

1. Wywołanie wybranego elementu `CopyToClipboard` funkcja elementu członkowskiego.

1. Jeśli użytkownik wybrał operacji wycinania, zamiast operacji kopiowania, usuwania wybranych danych z aplikacji.

Aby zapoznać się z przykładem tej sekwencji, zobacz `OnEditCut` i `OnEditCopy` funkcji OLE MFC przykładowe programy [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md). Należy pamiętać, że te przykłady konserwacji wskaźnik do danych aktualnie zaznaczonego, aby kroku 1 jest już ukończone.

##  <a name="_core_pasting_data"></a> Wklejanie danych

Wklejanie danych jest bardziej skomplikowane niż kopiowania go, ponieważ musisz wybrać format używany w wklejania danych w aplikacji.

#### <a name="to-paste-data-from-the-clipboard"></a>Wklejanie danych ze Schowka

1. W klasie widoku, należy zaimplementować `OnEditPaste` do obsługi użytkowników, wybierając opcję Wklej z menu Edycja.

1. W `OnEditPaste` funkcji, Utwórz `COleDataObject` obiektu, a następnie wywołać jej `AttachClipboard` funkcja elementu członkowskiego, aby połączyć ten obiekt danych do Schowka.

1. Wywołaj `COleDataObject::IsDataAvailable` do sprawdzenia, czy w określonym formacie jest dostępna.

   Alternatywnie możesz użyć `COleDataObject::BeginEnumFormats` do wyszukania w innych formatach, aż znajdziesz najbardziej odpowiednie dla aplikacji.

1. Wkleić formatu.

Aby uzyskać przykład sposobu działania, zobacz wykonania `OnEditPaste` funkcje Członkowskie w klas widoków zdefiniowanych w MFC OLE przykładowych programów [OCLIENT](../visual-cpp-samples.md) i [HIERSVR](../visual-cpp-samples.md).

> [!TIP]
>  Główną zaletą oddzielenie operacji wklejania do jego własnej funkcji jest, że ten sam kod Wklej mogą być używane po upuszczeniu danych w aplikacji podczas operacji przeciągania i upuszczania. Jak OCLIENT i HIERSVR Twoje `OnDrop` funkcji można również wywołać `DoPasteItem`, ponowne użycie kodu zapisywane do implementowania operacji wklejania.

Aby obsłużyć Wklej specjalne opcji menu Edycja, zobacz temat [okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)

- [Źródła danych OLE obiekty i dane oraz jednolitego transferów danych](../mfc/data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Zobacz też

[Schowek: korzystanie z mechanizmu schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

