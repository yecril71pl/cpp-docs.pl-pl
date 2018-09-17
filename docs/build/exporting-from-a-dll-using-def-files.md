---
title: Eksportowanie z biblioteki DLL przy użyciu plików DEF | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22bcca929d687ef3b10ee65bcb2230c03bfb0a11
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706007"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Eksportowanie z biblioteki DLL przy użyciu plików DEF

Plik definicji modułu (.def) jest plikiem tekstowym zawierającym jedną lub więcej instrukcji modułu, które opisują różne atrybuty pliku DLL. Jeśli nie używasz **__declspec(dllexport)** — słowo kluczowe do eksportowania funkcji DLL, biblioteka DLL wymaga pliku .def.

Minimalny pliku .def musi zawierać następujące instrukcje definicji modułów:

- Pierwsza instrukcja w pliku musi być instrukcją LIBRARY. Ta instrukcja identyfikuje plik .def jako należący do DLL. Po instrukcji LIBRARY następuje nazwa biblioteki DLL. Program łączący umieszcza tę nazwę w bibliotece importu biblioteki DLL.

- Instrukcja EXPORTS Wyświetla listę nazw i, opcjonalnie, wartości porządkowe funkcji eksportowanych przez DLL. Przypisujesz funkcji wartość porządkową przez następujące nazwy funkcji za pomocą znakiem (@) i numer. Kiedy określasz wartości porządkowe, muszą być z zakresu od 1 do N, gdzie N to liczba funkcji eksportowanych przez DLL. Jeśli chcesz wyeksportować funkcje według liczby porządkowej, zobacz [eksportowanie funkcji z biblioteki DLL według liczby porządkowej zamiast nazwy](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) a także w tym temacie.

Na przykład bibliotekę DLL, która zawiera kod implementujący drzewo binarnego wyszukiwania może wyglądać następująco:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Jeśli używasz [kreatora MFC DLL](../mfc/reference/mfc-dll-wizard.md) do utworzenia biblioteki MFC DLL, Kreator tworzy plik .def szkieletu i automatycznie dodaje do projektu. Dodaj nazwy funkcji, które mają zostać wyeksportowane do tego pliku. DLL bez MFC, należy samodzielnie utworzyć plik .def i dodać go do projektu.

Jeśli eksportujesz funkcje w pliku C++, musisz umieścić nazwy dekorowane w pliku .def lub zdefiniować funkcje eksportowania ze standardowym sprzężeniem C za pomocą funkcji extern "C". Jeśli musisz umieścić nazwę uzupełnioną w pliku .def, możesz je uzyskać, korzystając z [DUMPBIN](../build/reference/dumpbin-reference.md) narzędzia lub przy użyciu konsolidator [/MAP](../build/reference/map-generate-mapfile.md) opcji. Należy zauważyć, że nazwy dekoracyjne wytworzone przez kompilator są specyficzne dla kompilatora. Jeśli umieścisz nazwy dekoracyjne wytworzone przez kompilator języka Visual C++ w pliku .def, aplikacje, które łącze do biblioteki DLL muszą być także kompilowane przy użyciu tej samej wersji programu Visual C++, nazwy dekorowane w aplikacji wywołującej odpowiadały nazwom eksportowanym w regionalne biblioteki DLL Plik f.

Jeśli tworzysz [biblioteki DLL rozszerzenia](../build/extension-dlls-overview.md), i eksportujesz używając pliku .def, umieść następujący kod na początku i końcu plików nagłówka zawierających eksportowane klasy:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Linie te zapewniają, że zmienne MFC używane wewnętrznie lub dodawane do Twoich klas są eksportowane (lub importowane) z Twojego DLL rozszerzenia MFC. Na przykład kiedy uzyskujesz klasę za pomocą `DECLARE_DYNAMIC`, makro rozszerza się, aby dodać `CRuntimeClass` zmiennej składowej do swojej klasy. Pomijając tych czterech linii może spowodować bibliotekę DLL do kompilacji lub niepoprawne łączenie lub spowodować wystąpienie błędu, gdy aplikacja kliencka łączy do biblioteki DLL.

Podczas kompilowania biblioteki DLL, konsolidator używa fliku.def, aby utworzyć plik eksportowy (.exp) i plik importu biblioteki (.lib). Program łączący następnie używa pliku eksportu do tworzenia pliku DLL. Pliki wykonywalne, zawierające niejawne łącze do łącza biblioteki DLL do biblioteki importu, jeśli zostały one utworzone.

Należy pamiętać, że MFC sam używa plików .def, aby wyeksportować funkcje i klasy z MFCx0.dll.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL przy użyciu atrybutu __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu makra AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [Eksportuj funkcje C++ do użycia w plikach wykonywalnych języka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportuj funkcje C do użycia w plikach wykonywalnych języka C lub języka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określić, której metody eksportowania użyjesz](../build/determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)

- [Zainicjuj bibliotekę DLL](../build/run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [.def — pliki](../build/reference/module-definition-dot-def-files.md)

- [Zasady dla instrukcji definicji modułu](../build/reference/rules-for-module-definition-statements.md)

- [Nazwy ozdobione](../build/reference/decorated-names.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](../build/importing-and-exporting-inline-functions.md)

- [Importy wzajemne](../build/mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)