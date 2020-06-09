---
title: 'Schowek: kopiowanie i wklejanie danych'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: ed3056ec4fb3d3098870a03522d3bf17f41fbe34
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620704"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schowek: kopiowanie i wklejanie danych

W tym temacie opisano minimalną ilość pracy wymaganą do zaimplementowania kopiowania do i wklejania ze schowka w aplikacji OLE. Zaleca się przeczytanie tematów [obiektów danych i źródeł danych (OLE)](data-objects-and-data-sources-ole.md) przed kontynuowaniem.

Przed zaimplementowaniem kopiowania lub wklejania należy najpierw udostępnić funkcje do obsługi opcji kopiowania, wycinania i wklejania w menu Edycja.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Kopiowanie lub wycinanie danych

#### <a name="to-copy-data-to-the-clipboard"></a>Aby skopiować dane do schowka

1. Ustal, czy dane, które mają zostać skopiowane, to dane natywne, czy też element osadzony lub połączony.

   - Jeśli dane są osadzone lub połączone, uzyskaj wskaźnik do `COleClientItem` obiektu, który został wybrany.

   - Jeśli dane są natywne i aplikacja jest serwerem, Utwórz nowy obiekt pochodzący z `COleServerItem` zawierający wybrane dane. W przeciwnym razie Utwórz `COleDataSource` obiekt dla danych.

1. Wywołaj `CopyToClipboard` funkcję członkowską wybranego elementu.

1. Jeśli użytkownik wybrał operację wycinania zamiast operacji kopiowania, Usuń wybrane dane z aplikacji.

Aby zobaczyć przykład tej sekwencji, zobacz `OnEditCut` i `OnEditCopy` funkcje w przykładowych programach MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md). Należy zauważyć, że te przykłady utrzymują wskaźnik do aktualnie wybranych danych, więc krok 1 jest już ukończony.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Wklejanie danych

Wklejanie danych jest bardziej skomplikowane niż kopiowanie, ponieważ należy wybrać format do użycia podczas wklejania danych do aplikacji.

#### <a name="to-paste-data-from-the-clipboard"></a>Aby wkleić dane ze schowka

1. W klasie widoku Zaimplementuj, `OnEditPaste` Aby obsłużyć użytkownikom wybranie opcji Wklej z menu Edycja.

1. W `OnEditPaste` funkcji Utwórz `COleDataObject` obiekt i Wywołaj jego `AttachClipboard` funkcję członkowską, aby połączyć ten obiekt z danymi w Schowku.

1. Wywołaj `COleDataObject::IsDataAvailable` , aby sprawdzić, czy określony format jest dostępny.

   Alternatywnie, możesz użyć, `COleDataObject::BeginEnumFormats` Aby wyszukać inne formaty do momentu, gdy okaże się to najbardziej odpowiednie dla aplikacji.

1. Wykonaj wklejenie formatu.

Aby zapoznać się z przykładem tego, jak to działa, zobacz Implementacja `OnEditPaste` funkcji Członkowskich w klasach widoków zdefiniowanych w przykładowych programach MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) i [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> Główną zaletą oddzielenia operacji wklejenia do własnej funkcji jest to, że ten sam kod wklejania może być używany podczas usuwania danych w aplikacji podczas operacji przeciągania i upuszczania. Podobnie jak w OCLIENT i HIERSVR, `OnDrop` Funkcja może również wywołać `DoPasteItem` , ponownie użyć kodu zapisaną w celu zaimplementowania operacji wklejania.

Aby obsłużyć opcję Wklej specjalnie w menu Edycja, zobacz [okna dialogowe tematu w OLE](dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Dodawanie innych formatów](clipboard-adding-other-formats.md)

- [Obiekty danych OLE i źródła danych oraz jednolity transfer danych](data-objects-and-data-sources-ole.md)

- [Przeciąganie i upuszczanie elementów OLE](drag-and-drop-ole.md)

- [OLE](ole-background.md)

## <a name="see-also"></a>Zobacz też

[Schowek: korzystanie z mechanizmu schowka OLE](clipboard-using-the-ole-clipboard-mechanism.md)
