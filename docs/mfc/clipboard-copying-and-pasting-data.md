---
title: 'Schowek: kopiowanie i wklejanie danych'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374573"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schowek: kopiowanie i wklejanie danych

W tym temacie opisano minimalną pracę niezbędną do zaimplementowania kopiowania i wklejania ze Schowka w aplikacji OLE. Zaleca się przeczytanie obiektów [danych i źródeł danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) tematy przed kontynuowaniem.

Przed zaimplementowanie kopiowania lub wklejania należy najpierw podać funkcje obsługi opcji Kopiowanie, Wycinanie i Wklejanie w menu Edycja.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Kopiowanie lub cięcie danych

#### <a name="to-copy-data-to-the-clipboard"></a>Aby skopiować dane do Schowka

1. Określ, czy dane do skopiowania są danymi macierzystymi, czy są elementem osadzonym lub połączonym.

   - Jeśli dane są osadzone lub połączone, `COleClientItem` uzyskaj wskaźnik do wybranego obiektu.

   - Jeśli dane są natywne, a aplikacja jest serwerem, utwórz nowy obiekt pochodzący z `COleServerItem` zawierającego wybrane dane. W przeciwnym `COleDataSource` razie utwórz obiekt dla danych.

1. Wywołanie funkcji `CopyToClipboard` elementu członkowskiego wybranego elementu.

1. Jeśli użytkownik wybrał operację Wytnij zamiast operacji kopiowania, usuń wybrane dane z aplikacji.

Aby zobaczyć przykład tej `OnEditCut` sekwencji, `OnEditCopy` zobacz i funkcje w przykładowych programach MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md). Należy zauważyć, że te przykłady zachowują wskaźnik do aktualnie wybranych danych, więc krok 1 jest już ukończony.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Wklejanie danych

Wklejanie danych jest bardziej skomplikowane niż kopiowanie, ponieważ należy wybrać format do użycia przy wklejaniu danych do aplikacji.

#### <a name="to-paste-data-from-the-clipboard"></a>Aby wkleić dane ze Schowka

1. W klasie widoku `OnEditPaste` zaimplementuj do obsługi użytkowników wybierających opcję Wklej z menu Edycja.

1. W `OnEditPaste` funkcji utwórz `COleDataObject` obiekt i `AttachClipboard` wywołaj jego funkcję elementu członkowskiego, aby połączyć ten obiekt z danymi w Schowku.

1. Zadzwoń, `COleDataObject::IsDataAvailable` aby sprawdzić, czy dany format jest dostępny.

   Alternatywnie można użyć `COleDataObject::BeginEnumFormats` do wyszukiwania innych formatów, dopóki nie znajdziesz jeden najbardziej odpowiedni dla aplikacji.

1. Wykonaj wklej format.

Na przykład, jak to działa, zobacz `OnEditPaste` implementację funkcji elementu członkowskiego w klasach widoku zdefiniowanych w przykładowych programach MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> Główną zaletą oddzielenia operacji wklejania do własnej funkcji jest to, że ten sam kod wklejania może być używany, gdy dane są upuszczane w aplikacji podczas operacji przeciągania i upuszczania. Podobnie jak w OCLIENT i `OnDrop` HIERSVR, funkcja może również wywołać, `DoPasteItem`ponowneużywanie kodu napisanego w celu zaimplementowania operacji wklejania.

Aby obsłużyć opcję Wklej specjalnie w menu Edycja, zobacz temat [Okna dialogowe w OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)

- [Obiekty danych OLE i źródła danych oraz jednolity transfer danych](../mfc/data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie elementów OLE](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Zobacz też

[Schowek: korzystanie z mechanizmu schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
