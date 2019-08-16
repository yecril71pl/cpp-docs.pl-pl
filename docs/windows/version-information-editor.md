---
title: Edytor informacji o wersjiC++()
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: e68e1480d2cd9a8d8a4d862252e6eb4384a5cd68
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513643"
---
# <a name="version-information-editor-c"></a>Edytor informacji o wersjiC++()

Informacje o wersji obejmują tożsamość firmy i produktu, numer wydania produktu oraz powiadomienia o prawach autorskich i znakach towarowych. Za pomocą **edytora informacji o wersji**można tworzyć i obsługiwać te dane, które są przechowywane w zasobie informacji o wersji. Zasób informacji o wersji nie jest wymagany przez aplikację, ale jest przydatny do zbierania informacji identyfikujących aplikację. Informacje o wersji są również używane przez interfejsy API Instalatora.

> [!NOTE]
> Standard systemu Windows ma mieć tylko jeden zasób wersji o nazwie VS_VERSION_INFO.

Zasób informacji o wersji ma górny blok i co najmniej jeden niższy blok: pojedynczy blok informacji o ustalonym rozmiarze w górnej części i co najmniej jeden blok informacji o wersji na dole (dla innych języków i/lub zestawów znaków). Górny blok ma zarówno edytowalne pola liczbowe, jak i listę rozwijaną z możliwością wyboru. Dolne bloki mają tylko edytowalne pola tekstowe.

> [!NOTE]
> Korzystając z **edytora informacji o wersji**, w wielu wystąpieniach można kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń dotyczących zasobów. Na przykład jeśli wybierzesz pozycję podczas wskazywania wpisu nagłówka bloku, menu skrótów wyświetli **nowe informacje o bloku wersji** i **Usuń wersję bloku informacji** .

## <a name="how-to"></a>Instrukcje

**Edytor informacji o wersji** umożliwia:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Aby edytować ciąg w zasobie informacji o wersji

Wybierz element raz, aby go wybrać, a następnie ponownie, aby rozpocząć jego edytowanie. Wprowadzanie zmian bezpośrednio w tabeli **informacji o wersji** lub w [okno właściwości](/visualstudio/ide/reference/properties-window). Wprowadzone zmiany zostaną odzwierciedlone w obu miejscach.

Podczas edytowania `FILEFLAGS` klucza w **Edytorze informacji o wersji**należy zauważyć, że nie można ustawić **właściwości debugowania**, **prywatnej kompilacji**ani **specjalnej kompilacji** w oknie **Właściwości** dla plików. rc:

   - **Edytor informacji o wersji** ustawia `#ifdef` Właściwość **Debug** z w skrypcie `_DEBUG` zasobu na podstawie flagi Build.

  - `FILEFLAGS` Jeśli klucz ma ustawioną wartość w tabeli informacji o wersji, odpowiadająca jej Właściwość prywatnej kompilacji w oknie właściwości klucza będzie mieć wartość true. `Private Build` Jeśli **wartość** jest pusta, właściwość będzie mieć **wartość false**. Analogicznie, **specjalny klucz kompilacji** w tabeli **informacji o wersji** jest powiązany z specjalną właściwością `FILEFLAGS` **kompilacji** klucza.

Można sortować sekwencję informacji bloku ciągu, wybierając pozycję **klucz** lub nagłówki kolumn **wartości** . Te nagłówki automatycznie przestawiają informacje na wybraną sekwencję.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Aby dodać informacje o wersji dla innego języka (blok informacji o nowej wersji)

1. Otwórz zasób informacji o wersji, klikając go dwukrotnie w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli informacji o wersji i wybierz pozycję **nowy blok informacji o wersji**.

   To polecenie dodaje dodatkowy blok informacji do zasobu informacji o bieżącej wersji i otwiera odpowiednie właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window).

1. W oknie **Właściwości** wybierz odpowiedni język i zestaw znaków dla nowego bloku.

### <a name="to-delete-a-version-information-block"></a>Aby usunąć blok informacji o wersji

1. Otwórz zasób informacji o wersji, klikając dwukrotnie jego ikonę w [Widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy nagłówek bloku, który chcesz usunąć, i wybierz pozycję **Usuń wersję bloku informacji**.

   To polecenie powoduje usunięcie wybranego nagłówka i pozostawienie reszty informacji o wersji bez zmian. Nie można cofnąć akcji.

### <a name="to-access-version-information-from-within-your-program"></a>Aby uzyskać dostęp do informacji o wersji z poziomu programu

Jeśli chcesz uzyskać dostęp do informacji o wersji z poziomu programu, użyj funkcji [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) i funkcji [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) .

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Menu i inne zasoby](/windows/win32/menurc/resources)<br/>
[Informacje o wersji (Windows)](/windows/win32/menurc/version-information)
