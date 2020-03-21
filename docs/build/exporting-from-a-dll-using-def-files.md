---
title: Eksportowanie z biblioteki DLL przy użyciu plików DEF
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078521"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Eksportowanie z biblioteki DLL przy użyciu plików DEF

Plik definicji modułu lub DEF (*. def) jest plikiem tekstowym zawierającym jedną lub więcej instrukcji modułu, które opisują różne atrybuty biblioteki DLL. Jeśli nie używasz słowa kluczowego **__declspec (dllexport)** do eksportowania funkcji biblioteki DLL, biblioteka DLL wymaga pliku DEF.

Minimalny plik DEF musi zawierać następujące instrukcje definicji modułu:

- Pierwsza instrukcja w pliku musi być instrukcją biblioteki. Ta instrukcja identyfikuje plik DEF jako należący do biblioteki DLL. Po instrukcji biblioteki następuje nazwa biblioteki DLL. Konsolidator umieszcza tę nazwę w bibliotece importu biblioteki DLL.

- Instrukcja EXPORTs wyświetla listę nazw i, opcjonalnie, wartości porządkowe funkcji eksportowanych przez DLL. Przypisujesz funkcję do wartości porządkowej, wykonując nazwę funkcji ze znakiem (@) i liczbą. Po określeniu wartości porządkowych muszą one należeć do zakresu od 1 do N, gdzie N to liczba funkcji eksportowanych przez DLL. Jeśli chcesz eksportować funkcje według liczby porządkowej, zobacz [Eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie nazwy](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) , a także tego tematu.

Na przykład biblioteka DLL, która zawiera kod służący do implementowania binarnego drzewa wyszukiwania, może wyglądać następująco:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Jeśli użyjesz [kreatora MFC DLL](../mfc/reference/mfc-dll-wizard.md) do utworzenia biblioteki MFC DLL, Kreator tworzy plik szkieletu i automatycznie dodaje go do projektu. Dodaj nazwy funkcji, które mają zostać wyeksportowane do tego pliku. W przypadku bibliotek DLL innych niż MFC Utwórz sam plik DEF i dodaj go do projektu. Następnie przejdź do **właściwości** > **projektu** > **konsolidator** > **plik definicji modułu** **danych wejściowych** > i wprowadź nazwę pliku DEF. Powtórz ten krok dla każdej konfiguracji i platformy lub wykonaj wszystkie czynności jednocześnie, wybierając kolejno pozycje **Konfiguracja = wszystkie konfiguracje**i **platforma = wszystkie platformy**.

Jeśli eksportujesz funkcje w C++ pliku, musisz umieścić nazwy dekoracyjne w pliku DEF lub zdefiniować funkcje wyeksportowane za pomocą standardowego powiązania c, używając elementu extern "C". Jeśli trzeba umieścić nazwy dekoracyjne w pliku DEF, można je uzyskać za pomocą narzędzia [polecenia DUMPBIN](../build/reference/dumpbin-reference.md) lub za pomocą opcji konsolidatora [/map](../build/reference/map-generate-mapfile.md) . Należy zauważyć, że nazwy dekoracyjne wytwarzane przez kompilator są specyficzne dla kompilatora. Jeśli umieścisz nazwy dekoracyjne wytworzone przez kompilator C++ firmy Microsoft (MSVC) w pliku DEF, aplikacje łączące się z biblioteką DLL również muszą zostać skompilowane przy użyciu tej samej wersji programu MSVC, aby nazwy dekoracyjne w aplikacji wywołującej odpowiadały wyeksportowanym nazwom w pliku dll.

> [!NOTE]
> Biblioteka DLL skompilowana za pomocą programu Visual Studio 2015 może być używana przez aplikacje skompilowane z programem Visual Studio 2017 lub Visual Studio 2019.

W przypadku kompilowania [biblioteki DLL rozszerzenia](../build/extension-dlls-overview.md)i eksportowania przy użyciu pliku DEF należy umieścić Poniższy kod na początku i końcu plików nagłówkowych, które zawierają wyeksportowane klasy:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Te linie zapewniają, że zmienne MFC używane wewnętrznie lub dodawane do klas zostaną wyeksportowane (lub zaimportowane) z biblioteki DLL rozszerzenia MFC. Na przykład podczas wyprowadzania klasy przy użyciu `DECLARE_DYNAMIC`, makro rozszerza się, aby dodać `CRuntimeClass` zmienną członkowską do klasy. Pozostawienie tych czterech wierszy może spowodować, że biblioteka DLL zostanie skompilowana lub nawiązać nieprawidłowo lub przyczyną błędu, gdy aplikacja kliencka łączy się z biblioteką DLL.

Podczas kompilowania biblioteki DLL konsolidator używa pliku DEF do utworzenia pliku eksportu (. EXP) i pliku biblioteki importu (. lib). Konsolidator używa pliku eksportu do skompilowania pliku DLL. Pliki wykonywalne, które niejawnie łączą się z linkiem DLL do biblioteki importu podczas tworzenia.

Należy pamiętać, że MFC używa plików DEF do eksportowania funkcji i klas z MFCx0. dll.

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Eksportowanie z biblioteki DLL przy użyciu __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Eksportowanie i importowanie przy użyciu AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Funkcje C++ eksportu do użycia w plikach wykonywalnych języka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Eksportowanie funkcji języka C do użycia w plikach C++wykonywalnych języka c lub](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Określanie, której metody eksportowania użyć](determining-which-exporting-method-to-use.md)

- [Importowanie do aplikacji przy użyciu atrybutu __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicjowanie biblioteki DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [. def — pliki](reference/module-definition-dot-def-files.md)

- [Reguły dla instrukcji definicji modułu](reference/rules-for-module-definition-statements.md)

- [Nazwy dekoracyjne](reference/decorated-names.md)

- [Importowanie i eksportowanie funkcji śródwierszowych](importing-and-exporting-inline-functions.md)

- [Importy wzajemne](mutual-imports.md)

## <a name="see-also"></a>Zobacz też

[Eksportowanie z biblioteki DLL](exporting-from-a-dll.md)
