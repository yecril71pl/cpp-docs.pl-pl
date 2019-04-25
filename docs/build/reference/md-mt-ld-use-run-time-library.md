---
title: / MD, -MT, -LD (Korzystaj z bibliotek wykonawczych)
ms.date: 11/04/2016
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: 59b0483d76a2a98c1f278a323a827b243d21adea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321296"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)

Wskazuje, czy moduł wielowątkowy jest biblioteką DLL i określa wersje biblioteki wykonawczej handlowe lub przeznaczone do debugowania.

## <a name="syntax"></a>Składnia

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Uwagi

|Opcja|Opis|
|------------|-----------------|
|**/MD**|Powoduje, że aplikacja korzysta z wersji biblioteki wykonawczej specyficznej dla wielowątkowości i specyficznej dla DLL. Definiuje `_MT` i `_DLL` i powoduje, że kompilator umieszcza nazwę biblioteki MSVCRT.lib w pliku .obj.<br /><br /> Aplikacje skompilowane przy użyciu tej opcji są łączone statycznie z MSVCRT.lib. Ta biblioteka zawiera warstwę kodu, która umożliwia konsolidatorowi rozwiązywanie odwołań zewnętrznych. Rzeczywisty kod roboczy znajduje się w MSVCR*numerwersji*. Biblioteki DLL, która musi być dostępna w czasie wykonywania dla aplikacji łączonych z MSVCRT.lib.|
|**/MDd**|Definiuje `_DEBUG`, `_MT`, i `_DLL` i powoduje, że aplikacji do korzystania z wersji wielowątkowości dotyczące bibliotek DLL i debugowania biblioteki wykonawczej. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|
|**/MT**|Powoduje, że aplikacja korzysta ze statycznej, wielowątkowej wersji biblioteki wykonawczej. Definiuje `_MT` i powoduje, że kompilator umieszcza nazwę biblioteki LIBCMT.lib w pliku .obj, tak aby konsolidator użył LIBCMT.lib, aby rozwiązać zewnętrzne symbole.|
|**/MTd**|Definiuje `_DEBUG` i `_MT`. Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.|
|**/LD**|Tworzy DLL.<br /><br /> Przebiegi **/dll** opcję do konsolidatora. Konsolidator szuka, ale nie wymaga `DllMain` funkcji. Jeśli nie napiszesz `DllMain` funkcji, konsolidator wstawi `DllMain` funkcja, która zwraca wartość TRUE.<br /><br /> Łączy kod uruchamiający biblioteki DLL.<br /><br /> Tworzy bibliotekę importu (.lib), jeżeli nie określono pliku eksportu (.exp) w wierszu polecenia. Bibliotekę importu łączy się z aplikacjami, które wywołują bibliotekę DLL.<br /><br /> Interpretuje [/Fe (Nazwij plik EXE)](fe-name-exe-file.md) jako nazwę biblioteki DLL, a nie pliku .exe. Domyślnie nazwa programu staje się *basename*.dll zamiast *basename*.exe.<br /><br /> Oznacza **/MT** chyba że jawnie określisz **/MD**.|
|**/LDd**|Tworzy DLL przeznaczoną do debugowania. Definiuje `_MT` i `_DEBUG`.|

Aby uzyskać więcej informacji na temat biblioteki wykonawczej C i bibliotek, które są używane podczas kompilowania z [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](clr-common-language-runtime-compilation.md), zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

Wszystkie moduły przekazane do danego wywołania konsolidatora muszą być skompilowane przy użyciu tych samych opcji kompilatora biblioteki wykonawczej (**/MD**, **/MT**, **/LD**).

Aby uzyskać więcej informacji o sposobie używania wersji debugowania bibliotek uruchomieniowych, zobacz [odwołanie do biblioteki wykonawczej C](../../c-runtime-library/c-run-time-library-reference.md).

Aby uzyskać więcej informacji o bibliotekach DLL, zobacz [biblioteki dll w programie Visual C++](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **C/C++** folderu.

1. Wybierz **generowania kodu** stronę właściwości.

1. Modyfikowanie **biblioteki środowiska uruchomieniowego** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
