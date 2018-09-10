---
title: Opcje kompilatora i konsolidatora (C + +/ CX) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: ecfadce8-3a3f-40cc-bb01-b4731f8d2fcb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 086de927a6927087b8cbf3d1501ba6420e1027ed
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110808"
---
# <a name="compiler-and-linker-options-ccx"></a>Opcje kompilatora i konsolidatora (C + +/ CX)

Zmienna środowiskowa, C + +/ CX — opcje kompilatora i opcje konsolidatora obsługuje tworzenie aplikacji dla środowiska wykonawczego Windows.

## <a name="library-path"></a>Ścieżka biblioteki

Zmienna środowiskowa % LIBPATH % ścieżka domyślna do wyszukiwania plików winmd.

## <a name="compiler-options"></a>Opcje kompilatora

|Opcja|Opis|
|------------|-----------------|
|[/ZW](../build/reference/zw-windows-runtime-compilation.md)<br /><br /> /ZW:nostdlib|Włącza rozszerzenia językowe środowiska wykonawczego Windows.<br /><br /> `nostdlib` Parametr zapobiega przy użyciu ścieżki wyszukiwania standardowych, wstępnie zdefiniowanych można znaleźć zestawu i winmd przez kompilator.<br /><br /> **/ZW** — opcja kompilatora niejawnie określa następujące opcje kompilatora:<br /><br /> -   **/Fi** vccorlib.h, co zmusza włączenia vccorlib.h pliku nagłówkowego, który definiuje wiele typów, które są wymagane przez kompilator.<br />-   [/Fu](../build/reference/fu-name-forced-hash-using-file.md) Windows.winmd, co zmusza włączenia Windows.winmd plik metadanych, które są dostarczane przez system operacyjny, a następnie definiuje wiele typów środowiska wykonawczego Windows.<br />-   **/Fu** Platform.winmd, co zmusza włączenia Platform.winmd pliku metadanych, które są dostarczane przez kompilator, a następnie definiuje większość typów w przestrzeni nazw z rodziny platformy.|
|[/AI](../build/reference/ai-specify-metadata-directories.md) *dir*|Dodaje katalog, który jest określony przez *dir* parametru do ścieżki wyszukiwania, której kompilator używa do wyszukiwania plików zestawu i winmd.|
|**/Fu***pliku*|Wymusza umieszczenie określonym module lub plik winmd. Oznacza to, nie trzeba określać `#using` *pliku* w kodzie źródłowym. Kompilator automatycznie wymusza umieszczenie swój własny plik metadanych Windows Platform.winmd.|
|/D "WINAPI_FAMILY = 2"|Tworzy definicję, która umożliwia korzystanie z podzestawu Win32 SDK, który jest zgodny ze środowiskiem uruchomieniowym Windows.|

## <a name="linker-options"></a>Opcje konsolidatora

|Opcja|Opis|
|------------|-----------------|
|/ APPCONTAINER [: NO]|Oznacza plik wykonywalny jako możliwy do uruchomienia w kontenerze appcontainer (tylko).|
|/ WINMD [: {BRAK&AMP;#124;TYLKO}]|Generuje plik winmd i skojarzony plik binarny. Ta opcja muszą być przekazywane do konsolidatora do winmd maszynowych.<br /><br /> **NIE**— nie emituj pliku winmd, ale emitują pliku binarnego.<br /><br /> **TYLKO**— emituje pliku winmd, ale nie emituj pliku binarnego.|
|/ WINMDFILE:*nazwy pliku*|Nazwa pliku winmd do emitowania zamiast domyślnej nazwy pliku winmd. Jeśli nie określono wiele nazw plików w wierszu polecenia, ostatnia nazwa jest używana.|
|/WINMDDELAYSIGN[:NO]|Częściowo podpisuje plik winmd i umieszcza klucz publiczny w pliku binarnym.<br /><br /> **NIE**—(Default) nie podpisania pliku winmd.<br /><br /> / WINMDDELAYSIGN nie ma wpływu, chyba że /WINMDKEYFILE lub /WINMDKEYCONTAINER jest także określona.|
|/ WINMDKEYCONTAINER:*nazwy*|Określa kontener klucza do podpisywania zestawu. *Nazwa* parametr odnosi się do kontenera kluczy, który służy do podpisania pliku metadanych.|
|/ WINMDKEYFILE:*nazwy pliku*|Określa klucz lub parę kluczy do podpisywania zestawu. *Filename* parametr odnosi się do klucza, który służy do podpisania pliku metadanych.|

### <a name="remarks"></a>Uwagi

Kiedy używasz **/ZW**, kompilator automatycznie łączy się z wersją biblioteki DLL środowiska uruchomieniowego C (CRT). Łączenie wersji biblioteki statycznej nie jest dozwolone, a każde użycie funkcji CRT, które nie są dozwolone w aplikacji platformy uniwersalnej Windows spowoduje błąd w czasie kompilacji.

## <a name="see-also"></a>Zobacz też

[Tworzenie aplikacji i bibliotek](../cppcx/building-apps-and-libraries-c-cx.md)