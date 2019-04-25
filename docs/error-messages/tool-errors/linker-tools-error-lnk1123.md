---
title: Błąd narzędzi konsolidatora LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: b67a2a4ddad13988967b7cc7d827862a2a6fe933
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255232"
---
# <a name="linker-tools-error-lnk1123"></a>Błąd narzędzi konsolidatora LNK1123

> Wystąpił błąd podczas konwersji do formatu COFF: plik jest nieprawidłowy lub uszkodzony

Pliki wejściowe musi mieć format Common Object File Format (COFF). Jeśli plik wejściowy nie jest COFF, konsolidator automatycznie podejmuje próbę przekonwertowania obiektów OMF 32-bitowego do formatu COFF lub działa na błąd. EXE w celu konwersji plików zasobów. Ten komunikat oznacza, że konsolidator nie można skonwertować pliku. Może również wystąpić podczas korzystania z niezgodną wersję narzędzia CVTRES. EXE z innej instalacji programu Visual Studio, zestaw deweloperski Windows lub .NET Framework.

> [!NOTE]
> Jeśli używasz starszej wersji programu Visual Studio automatyczna konwersja nie może być obsługiwane.

## <a name="to-fix-the-problem"></a>Aby rozwiązać ten problem

- Zastosuj wszystkie dodatki service pack i aktualizacje dla używanej wersji programu Visual Studio. Jest to szczególnie ważne w przypadku programu Visual Studio 2010.

- Spróbować utworzyć z łączeniem przyrostowym wyłączone. Na pasku menu wybierz **projektu**, **właściwości**. W **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **konsolidatora**. Zmień wartość właściwości **Włącz konsolidację przyrostową** do **nie**.

- Upewnij się, że wersja narzędzia CVTRES. Znaleziono plik EXE najpierw w zmiennej środowiskowej PATH jest zgodna wersja narzędzia do kompilacji lub wersji zestawu narzędzi platformy, używaną w projekcie.

- Spróbuj wyłączyć opcję Osadzanie manifestu. Na pasku menu wybierz **projektu**, **właściwości**. W **stron właściwości** okna dialogowego rozwiń **właściwości konfiguracji**, **narzędziu manifestu**, **danych wejściowych i wyjściowych**. Zmień wartość właściwości **osadzanie manifestu** do **nie**.

- Upewnij się, że typ pliku jest prawidłowa. Na przykład upewnij się, że obiekt OMF jest 32-bitowe i nie 16-bitowych. Aby uzyskać więcej informacji, zobacz [. Pliki obj jako wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md) i [formatu PE](/windows/desktop/Debug/pe-format).

- Upewnij się, że plik nie jest uszkodzony. Ponownie skompiluj go, jeśli to konieczne.

## <a name="see-also"></a>Zobacz także

[Pliki .obj — wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)
