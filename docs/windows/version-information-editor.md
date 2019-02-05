---
title: Edytor informacji o wersji (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 94afb429af6eb1b0d570a444f49145a31c2fec1f
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742677"
---
# <a name="version-information-editor-c"></a>Edytor informacji o wersji (C++)

Informacje o wersji składa się z firmy i identyfikacji produktu, numer wersji produktu i praw autorskich i znak towarowy powiadomień. Za pomocą **informacje o wersji** edytora, możesz tworzyć i obsługiwać te dane, które jest przechowywane w zasobach informacji o wersji. Zasobach informacji o wersji nie jest wymagane przez aplikację, ale jest użytecznym miejscem, aby zebrać informacje identyfikujące aplikację. Informacje o wersji jest również używany przez Instalatora interfejsów API.

Zasobach informacji o wersji ma blokiem górnej i jeden lub więcej bloków niższe: jeden blok informacji stałej u góry i jeden lub więcej bloków informacyjnych wersji u dołu (w przypadku innych języków i/lub zestawów znaków). Blokuj najważniejsze ma edytowalnych pól liczbowych i list rozwijanych można wybrać. Niższe bloki zawierają tylko edytowalnymi polami tekstowymi.

> [!NOTE]
> Standardowa Windows jest tylko jedna wersja zasobu o nazwie VS_VERSION_INFO.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

**Informacje o wersji** Edytor pozwala:

## <a name="to-edit-a-string-in-a-version-information-resource"></a>Edytowanie ciągu w zasobach informacji o wersji

Wybierz element raz, aby następnie ponownie wybierz go, aby rozpocząć jego edycji. Wprowadź zmiany bezpośrednio w **informacje o wersji** tabeli lub [okno właściwości](/visualstudio/ide/reference/properties-window). Wprowadzone zmiany zostaną odzwierciedlone w obu miejscach.

   > [!NOTE]
   > Podczas edytowania `FILEFLAGS` w **informacje o wersji** edytora, zauważysz, nie można ustawić **debugowania**, **kompilacja prywatna**, lub **specjalne Tworzenie** właściwości (w **właściwości** okna) plików .rc:

   - **Informacje o wersji** zestawy edytora **debugowania** właściwość o `#ifdef` w skrypcie zasobów na podstawie `_DEBUG` kompilacji flagi.

   - Jeśli `Private Build` kluczu **wartość** w **informacje o wersji** tabeli, odpowiedni **kompilacja prywatna** właściwości (w **właściwości**  okna) dla `FILEFLAGS` klucz będzie **True**. Jeśli **wartość** jest pusta, właściwość będzie **False**. Podobnie **kompilacji specjalnych** klucza (w **informacje o wersji** tabeli) jest powiązana z **kompilacji specjalnych** właściwość `FILEFLAGS` klucza.

Sekwencji informacji bloku ciąg można sortować, klikając **klucz** lub **wartość** nagłówki kolumn. Te nagłówki automatyczne rozmieszczanie informacji w wybranej sekwencji.

## <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Aby dodać informacje o wersji dla innego języka (nowej wersję bloku informacyjnego)

1. Otwórz zasób informacje o wersji, klikając go dwukrotnie [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy w tabeli zawierającej informacje o wersji, a następnie wybierz **nowej wersję bloku informacyjnego** z menu skrótów.

   To polecenie dodaje do bieżącej zasobach informacji o wersji blok dodatkowe informacje i zostanie otwarty jego odpowiednie właściwości w [okno właściwości](/visualstudio/ide/reference/properties-window).

1. W **właściwości** okna, wybierz odpowiedni język i zestaw nowego bloku znaków.

## <a name="to-delete-a-version-information-block"></a>Aby usunąć blok informacji o wersji

1. Otwórz w zasobach informacji o wersji, klikając dwukrotnie odpowiednią ikonę w [widok zasobów](../windows/resource-view-window.md).

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

1. Kliknij prawym przyciskiem myszy nagłówek bloku chcesz usunąć, a następnie wybierz pozycję **Usuń wersję bloku informacyjnego** z menu skrótów.

   To polecenie usuwa wybrany nagłówek i pozostawia pozostałe informacje o wersji bez zmian. Nie można cofnąć akcję.

## <a name="to-access-version-information-from-within-your-program"></a>Aby uzyskać dostęp do informacji o wersji z Twojego programu

Aby uzyskać dostęp do informacji o wersji z Twojego programu, należy użyć [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) funkcji i [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) funkcji.

   > [!NOTE]
   > Podczas korzystania z **informacje o wersji** edytora w wielu przypadkach, kliknięcie prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Na przykład jeśli wybierzesz podczas wskazujący wpis nagłówka bloku pokazuje menu skrótów **nowe informacje o bloku wersji** i **usuwanie bloku informacji o wersji** poleceń.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Informacje o wersji (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)
