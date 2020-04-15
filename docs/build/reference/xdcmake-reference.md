---
title: XDCMake — odwołanie
ms.date: 11/04/2016
f1_keywords:
- xdcmake
helpviewer_keywords:
- xdcmake program
ms.assetid: 14e65747-d000-4343-854b-8393bf01cbac
ms.openlocfilehash: 9970470d1feb471f9e0b8c9284a08337dac7ef0f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335858"
---
# <a name="xdcmake-reference"></a>XDCMake — odwołanie

xdcmake.exe to program, który kompiluje pliki xdc w plik .xml. Plik xdc jest tworzony przez kompilator MSVC dla każdego pliku kodu źródłowego, gdy kod źródłowy jest kompilowany z [/doc](doc-process-documentation-comments-c-cpp.md) i gdy plik kodu źródłowego zawiera komentarze dokumentacji oznaczone tagami XML.

### <a name="to-use-xdcmakeexe-in-the-visual-studio-development-environment"></a>Aby użyć programu xdcmake.exe w środowisku programistycznym Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Otwórz folder **Właściwości konfiguracji.**

1. Kliknij stronę właściwości **Komentarze dokumentów XML.**

> [!NOTE]
> Opcje xdcmake.exe w wierszu polecenia różnią się od opcji, gdy xdcmake.exe jest używany w środowisku programistycznym (strony właściwości). Aby uzyskać informacje na temat używania pliku xdcmake.exe w środowisku programistycznym, zobacz [Strony właściwości narzędzia generatora dokumentów XML](xml-document-generator-tool-property-pages.md).

## <a name="syntax"></a>Składnia

xdcmake ( xdcmake )`input_filename options`

## <a name="parameters"></a>Parametry

*input_filename*<br/>
Nazwa pliku .xdc używana jako dane wejściowe do pliku xdcmake.exe. Określ jeden lub więcej plików xdc lub użyj *.xdc, aby użyć wszystkich plików xdc w bieżącym katalogu.

*Opcje*<br/>
Zero lub więcej z następujących czynności:

|Opcja|Opis|
|------------|-----------------|
|/?, /help|Wyświetl pomoc dla xdcmake.exe.|
|/assembly:*nazwa pliku*|Umożliwia określenie wartości znacznika \<> złożenia w pliku xml.  Domyślnie wartość \<zestawu> tag jest taka sama jak nazwa pliku xml.|
|/nologo|Pomiń wiadomości dotyczące praw autorskich.|
|/out:*nazwa pliku*|Umożliwia określenie nazwy pliku xml.  Domyślnie nazwa pliku xml jest nazwą pliku xdc pierwszego pliku xdc przetwarzanego przez xdcmake.exe.|

## <a name="remarks"></a>Uwagi

Visual Studio wywoła xdcmake.exe automatycznie podczas tworzenia projektu. Można również wywołać xdcmake.exe w wierszu polecenia.

Aby uzyskać więcej informacji na temat dodawania komentarzy do dokumentacji do plików kodu źródłowego, zobacz [Polecane znaczniki dla komentarzy do dokumentacji.](recommended-tags-for-documentation-comments-visual-cpp.md)

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](xml-documentation-visual-cpp.md)
