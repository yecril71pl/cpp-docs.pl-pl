---
title: 'Schowek: Korzystanie z mechanizmu Schowka OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], Clipboard
- OLE Clipboard
- Clipboard [MFC], OLE formats
- OLE Clipboard, formats
- formats [MFC], Clipboard for OLE
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
ms.openlocfilehash: 0f2c10f4a88b723d1ab9f4bb0ca903987359c9fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508906"
---
# <a name="clipboard-using-the-ole-clipboard-mechanism"></a>Schowek: Korzystanie z mechanizmu Schowka OLE

Technologia OLE używa formatów standardowych i niektórych formatów specyficznych dla OLE do przesyłania danych za pośrednictwem Schowka.

Podczas wycinania lub kopiowania danych z aplikacji dane są przechowywane w schowku do późniejszego użycia w operacjach wklejania. Te dane są w różnych formatach. Gdy użytkownik zdecyduje się wkleić dane ze schowka, aplikacja może wybrać, które z tych formatów użyć. Aplikacja powinna zostać zapisywana w celu wybrania formatu, który zapewnia najwięcej informacji, chyba że użytkownik zażąda określonego formatu przy użyciu opcji Wklej specjalnie. Przed kontynuowaniem warto przeczytać temat [obiekty danych i źródła danych (OLE)](../mfc/data-objects-and-data-sources-ole.md) . Opisano w nim podstawowe informacje o sposobie przesyłania danych i sposobach ich implementacji w aplikacjach.

System Windows definiuje szereg standardowych formatów, które mogą być używane do przesyłania danych za pomocą Schowka. Są to m.in. pliki, tekst, mapy bitowe i inne. OLE definiuje również wiele formatów specyficznych dla OLE. W przypadku aplikacji, które wymagają większej szczegółowości niż podane w standardowych formatach, dobrym pomysłem jest zarejestrowanie własnych niestandardowych formatów Schowka. Użyj funkcji Win32 API, [](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) aby to zrobić.

Na przykład program Microsoft Excel rejestruje niestandardowy format dla arkuszy kalkulacyjnych. Ten format wykonuje więcej informacji niż na przykład mapa bitowa. Gdy dane zostaną wklejone do aplikacji, która obsługuje format arkusza kalkulacyjnego, wszystkie formuły i wartości z arkusza kalkulacyjnego są zachowywane i można je zaktualizować w razie potrzeby. Program Microsoft Excel umieszcza również dane w schowku w formatach, dzięki czemu można je wkleić jako element OLE. Każdy kontener dokumentu OLE może wkleić te informacje jako element osadzony. Ten osadzony element można zmienić przy użyciu programu Microsoft Excel. Schowek zawiera również prostą mapę bitową obrazu zaznaczonego zakresu w arkuszu kalkulacyjnym. Można to również wkleić do kontenerów dokumentów OLE lub do edytorów map bitowych, takich jak Paint. W przypadku mapy bitowej nie ma jednak możliwości manipulowania danymi w postaci arkusza kalkulacyjnego.

Aby pobrać maksymalną ilość informacji ze schowka, aplikacje powinny sprawdzić te formaty niestandardowe przed wklejeniem danych ze schowka.

Na przykład, aby włączyć polecenie Wytnij, można napisać procedurę obsługi podobną do następującej:

[!code-cpp[NVC_MFCListView#3](../atl/reference/codesnippet/cpp/clipboard-using-the-ole-clipboard-mechanism_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)

- [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)

- [Korzystanie ze schowka systemu Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [SERWERY](../mfc/ole-background.md)

- [Obiekty danych OLE i źródła danych oraz jednolity transfer danych](../mfc/data-objects-and-data-sources-ole.md)

## <a name="see-also"></a>Zobacz także

[Schowek](../mfc/clipboard.md)
