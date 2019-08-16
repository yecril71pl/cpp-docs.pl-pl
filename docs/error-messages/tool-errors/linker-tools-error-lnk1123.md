---
title: Błąd narzędzi konsolidatora LNK1123
ms.date: 12/29/2017
f1_keywords:
- LNK1123
helpviewer_keywords:
- LNK1123
ms.openlocfilehash: 31fd634291bfb0af17348197ae8a6225ac490c89
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509902"
---
# <a name="linker-tools-error-lnk1123"></a>Błąd narzędzi konsolidatora LNK1123

> Wystąpił błąd podczas konwersji do formatu COFF: plik jest nieprawidłowy lub uszkodzony

Pliki wejściowe muszą mieć format pliku (COFF) Common Object Format. Jeśli plik wejściowy nie jest plikiem COFF, konsolidator automatycznie próbuje skonwertować 32-bitowe obiekty OMF na COFF lub uruchomi CVTRES. EXE do konwersji plików zasobów. Ten komunikat oznacza, że konsolidator nie mógł skonwertować pliku. Może się to zdarzyć również w przypadku korzystania z niezgodnej wersji CVTRES. EXE z innej instalacji programu Visual Studio, zestawu Windows Development Kit lub .NET Framework.

> [!NOTE]
> Jeśli używasz wcześniejszej wersji programu Visual Studio, automatyczne konwertowanie może nie być obsługiwane.

## <a name="to-fix-the-problem"></a>Aby rozwiązać ten problem

- Zastosuj wszystkie dodatki Service Pack i aktualizacje dla używanej wersji programu Visual Studio. Jest to szczególnie ważne w przypadku programu Visual Studio 2010.

- Spróbuj skompilować przy użyciu linku przyrostowego wyłączone. Na pasku menu wybierz **projekt**, **Właściwości**. W oknie dialogowym **strony właściwości** rozwiń węzeł **Właściwości konfiguracji**, **konsolidator**. Zmień wartość **Włącz łączenie przyrostowe** na **nie**.

- Sprawdź, czy wersja programu CVTRES. Plik EXE znaleziono jako pierwszy w zmiennej środowiskowej PATH, dopasowuje się do wersji narzędzi do kompilacji lub wersji narzędzia platformy używanej przez Twój projekt.

- Spróbuj wyłączyć opcję Osadź manifest. Na pasku menu wybierz **projekt**, **Właściwości**. W oknie dialogowym **strony właściwości** rozwiń węzeł **Właściwości konfiguracji**, **narzędzie manifestu**, **dane wejściowe i wyjściowe**. Zmień wartość **manifestu osadzania** na **nie**.

- Upewnij się, że typ pliku jest prawidłowy. Na przykład upewnij się, że obiekt OMF jest 32-bitowy i nie jest 16-bitowy. Aby uzyskać więcej informacji, zobacz [. Pliki obj jako dane wejściowe konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md) i [Format PE](/windows/win32/Debug/pe-format).

- Upewnij się, że plik nie jest uszkodzony. W razie potrzeby Skompiluj ją ponownie.

## <a name="see-also"></a>Zobacz także

[Pliki .obj — wejście konsolidatora](../../build/reference/dot-obj-files-as-linker-input.md)<br/>
[EDITBIN — dokumentacja](../../build/reference/editbin-reference.md)<br/>
[DUMPBIN — dokumentacja](../../build/reference/dumpbin-reference.md)
