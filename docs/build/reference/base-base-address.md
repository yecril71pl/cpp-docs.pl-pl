---
title: /BASE (Adres podstawowy)
ms.date: 09/05/2018
f1_keywords:
- /base
- VC.Project.VCLinkerTool.BaseAddress
helpviewer_keywords:
- base addresses [C++]
- programs [C++], preventing relocation
- semicolon [C++], specifier
- -BASE linker option
- key address size
- environment variables [C++], LIB
- programs [C++], base address
- LIB environment variable
- BASE linker option
- DLLs [C++], linking
- /BASE linker option
- '@ symbol for base address'
- executable files [C++], base address
- at sign symbol for base address
ms.assetid: 00b9f6fe-0bd2-4772-a69c-7365eb199069
ms.openlocfilehash: dc6380903af0be2e6696ca3589813c249f71dd05
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341023"
---
# <a name="base-base-address"></a>/BASE (Adres podstawowy)

Określa adres bazowy programu.

## <a name="syntax"></a>Składnia

> **/ BASE:**{*adres*[**,**<em>rozmiar</em>] | **\@** <em>filename</em>**,**<em>klucz</em>}

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Ze względów bezpieczeństwa firma Microsoft zaleca, możesz użyć [opcja/DynamicBase](dynamicbase-use-address-space-layout-randomization.md) opcji zamiast określania adresami podstawowymi dla usługi plików wykonywalnych. Spowoduje to wygenerowanie pliku wykonywalnego obrazu, który może być losowo przebazowanych w czasie ładowania przy użyciu funkcji randomizacji (ASLR) adres miejsca układu systemu Windows. Opcja/DynamicBase — opcja jest domyślnie włączone.

/ PODSTAWOWYCH opcji ustawia adres bazowy programu zastępowanie domyślną lokalizację dla pliku .exe lub DLL. Domyślny adres podstawowy dla pliku .exe jest 0x400000 dla 32-bitowych obrazów lub 0x140000000 dla 64-bitowych obrazów. Dla bibliotek DLL z adres bazowy domyślną jest 0x10000000 dla 32-bitowych obrazów lub 0x180000000 dla 64-bitowych obrazów. W systemach operacyjnych, które nie obsługują randomizacji układu przestrzeni adresowej (ASLR) lub jeśli opcja: no została ustawiona system operacyjny najpierw próbuje załadować programu pod jego określonego lub adres bazowy domyślną. Jeśli wystarczającą ilość miejsca jest niedostępny w istnieje, system przenosi program. Aby uniknąć przenoszenia, należy użyć [/FIXED](fixed-fixed-base-address.md) opcji.

Konsolidator generuje błąd, jeśli *adres* nie jest wielokrotnością 64 KB. Opcjonalnie można określić rozmiar program konsolidator generuje ostrzeżenie, jeśli program nie mieści się w podany rozmiar.

W wierszu polecenia innym sposobem określenia adres podstawowy jest przy użyciu pliku odpowiedzi z adresu podstawowego. Adres podstawowy plik odpowiedzi jest plik tekstowy, który zawiera adres podstawowy i opcjonalnie rozmiarów wszystkie biblioteki dll będzie używać programu i klucz unikatowy tekst dla każdego adresu podstawowego. Aby określić adres bazowy przy użyciu pliku odpowiedzi, należy użyć znakiem (**\@**) i nazwa pliku odpowiedzi *filename*, a następnie przecinek, a następnie *klucz*wartość dla podstawowego adresu do użycia w pliku. Konsolidator szuka *filename* w obu określonej ścieżce, lub jeśli ścieżka nie zostanie określona w katalogach określonych w zmiennej środowiskowej LIB. Każdy wiersz w *filename* reprezentuje jedną bibliotekę DLL, a ma następującą składnię:

> *klucz* *adres* [*rozmiar*] **;** *komentarz*

*Klucz* ciąg znaków alfanumerycznych i nie jest uwzględniana wielkość liter. Zazwyczaj jest to nazwa biblioteki dll, ale nie muszą być. *Klucz* następuje podstawowej *adres* w notacji języka C, szesnastkowym lub dziesiętną i opcjonalnie maksymalnie *rozmiar*. Wszystkie trzy argumenty są oddzielone tabulacji lub spacji. Konsolidator generuje ostrzeżenie, jeśli określony *rozmiar* jest mniejsza niż wirtualnej przestrzeni adresowej wymagane przez program. A *komentarz* określono za pomocą średnika (**;**) i może być na tym samym lub w osobnym wierszu. Konsolidator ignoruje cały tekst z średnik z powrotem do końca wiersza. W tym przykładzie przedstawiono część tego pliku:

```
main   0x00010000    0x08000000    ; for PROJECT.exe
one    0x28000000    0x00100000    ; for DLLONE.DLL
two    0x28100000    0x00300000    ; for DLLTWO.DLL
```

Jeśli plik, który zawiera następujące wiersze, zostanie wywołany DLLS.txt, następujące przykładowe polecenie mają zastosowanie te informacje:

```
link dlltwo.obj /dll /base:@dlls.txt,two
```

Innym sposobem, aby ustawić adres podstawowy jest za pomocą *podstawowy* argument [nazwa](name-c-cpp.md) lub [biblioteki](library.md) instrukcji. Uwzględniają i [/dll](dll-build-a-dll.md) opcje razem są równoważne **biblioteki** instrukcji.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** > **zaawansowane** stronę właściwości.

1. Modyfikowanie **adresu podstawowego** właściwości.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.BaseAddress%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
