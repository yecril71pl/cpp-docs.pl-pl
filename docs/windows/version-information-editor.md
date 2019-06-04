---
title: Edytor informacji o wersji (C++)
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
ms.openlocfilehash: a17539d0a9fb94c440d65275e9d032182088ae6e
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504484"
---
# <a name="version-information-editor-c"></a>Edytor informacji o wersji (C++)

Informacje o wersji składa się z firmy i identyfikacji produktu, numer wersji produktu i praw autorskich i znak towarowy powiadomień. Za pomocą **Edytor informacji o wersji**, tworzenia i przechowywania tych danych, który jest przechowywany w zasobach informacji o wersji. Zasobach informacji o wersji nie jest wymagane przez aplikację, ale jest użytecznym miejscem, aby zebrać informacje identyfikujące aplikację. Informacje o wersji jest również używany przez Instalatora interfejsów API.

> [!NOTE]
> Standardowa Windows jest tylko jedna wersja zasobu o nazwie VS_VERSION_INFO.

Zasobach informacji o wersji ma blokiem górnej i jeden lub więcej bloków niższe: jeden blok informacji stałej u góry i jeden lub więcej bloków informacyjnych wersji u dołu (w przypadku innych języków i/lub zestawów znaków). Blokuj najważniejsze ma edytowalnych pól liczbowych i list rozwijanych można wybrać. Niższe bloki zawierają tylko edytowalnymi polami tekstowymi.

> [!NOTE]
> Podczas korzystania z **Edytor informacji o wersji**, w wielu przypadkach możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Na przykład jeśli wybierzesz podczas wskazujący wpis nagłówka bloku pokazuje menu skrótów **nowe informacje o bloku wersji** i **usuwanie bloku informacji o wersji** poleceń.

## <a name="how-to"></a>Instrukcje

**Edytor informacji o wersji** umożliwia:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Edytowanie ciągu w zasobach informacji o wersji

Wybierz element raz, aby następnie ponownie wybierz go, aby rozpocząć jego edycji. Wprowadź zmiany bezpośrednio w **informacje o wersji** tabeli lub [okno właściwości](/visualstudio/ide/reference/properties-window). Wprowadzone zmiany zostaną odzwierciedlone w obu miejscach.

Podczas edytowania `FILEFLAGS` w **Edytor informacji o wersji**, zwróć uwagę, nie można ustawić **debugowania**, **kompilacja prywatna**, lub **specjalne kompilacji**  właściwości w **właściwości** okna dla plików .rc:

   - **Edytor informacji o wersji** ustawia **debugowania** właściwość o `#ifdef` w skrypcie zasobów na podstawie `_DEBUG` kompilacji flagi.

  - Jeśli `Private Build` kluczu **wartość** w **informacje o wersji** tabeli, odpowiedni **kompilacja prywatna** właściwość **właściwości**  okno `FILEFLAGS` klucz będzie **True**. Jeśli **wartość** jest pusta, właściwość będzie **False**. Podobnie **kompilacji specjalnych** w **informacje o wersji** tabela jest powiązana z **kompilacji specjalnych** właściwość `FILEFLAGS` klucza.

Sekwencja informacji blok ciągu można sortować, wybierając opcję **klucz** lub **wartość** nagłówki kolumn. Te nagłówki automatyczne rozmieszczanie informacji w wybranej sekwencji.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Aby dodać informacje o wersji dla innego języka (nowej wersję bloku informacyjnego)

1. Otwórz zasób informacje o wersji, klikając go dwukrotnie [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy w tabeli zawierającej informacje o wersji, a następnie wybierz **nowej wersję bloku informacyjnego**.

   To polecenie dodaje do bieżącej zasobach informacji o wersji blok dodatkowe informacje i zostanie otwarty jego odpowiednie właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window).

1. W **właściwości** okna, wybierz odpowiedni język i zestaw nowego bloku znaków.

### <a name="to-delete-a-version-information-block"></a>Aby usunąć blok informacji o wersji

1. Otwórz w zasobach informacji o wersji, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](how-to-create-a-resource-script-file.md#create-resources).

1. Kliknij prawym przyciskiem myszy nagłówek bloku chcesz usunąć, a następnie wybierz **Usuń wersję bloku informacyjnego**.

   To polecenie usuwa wybrany nagłówek i pozostawia pozostałe informacje o wersji bez zmian. Nie można cofnąć akcję.

### <a name="to-access-version-information-from-within-your-program"></a>Aby uzyskać dostęp do informacji o wersji z Twojego programu

Aby uzyskać dostęp do informacji o wersji z Twojego programu, należy użyć [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) funkcji i [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) funkcji.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Menu i inne zasoby](/windows/desktop/menurc/resources)<br/>
[Informacje o wersji (Windows)](/windows/desktop/menurc/version-information)
