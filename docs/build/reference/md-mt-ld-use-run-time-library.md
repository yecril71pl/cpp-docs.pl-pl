---
title: /MD,-MT,-LD (Korzystaj z bibliotek Run-Time)
ms.date: 07/17/2019
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
ms.openlocfilehash: a66677ebbef984e9a4c8190f184ca3a9126a7b83
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550761"
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
|**/MD**|Powoduje, że aplikacja korzysta z wersji biblioteki wykonawczej specyficznej dla wielowątkowości i specyficznej dla DLL. Definiuje `_MT` i `_DLL` i powoduje, że kompilator umieszcza nazwę biblioteki Msvcrt. lib w pliku. obj.<br /><br /> Aplikacje skompilowane przy użyciu tej opcji są łączone statycznie z MSVCRT.lib. Ta biblioteka zawiera warstwę kodu, która umożliwia konsolidatorowi rozwiązywanie odwołań zewnętrznych. Rzeczywisty kod roboczy jest zawarty w pliku MSVCR*versionNumber*. Biblioteka DLL, która musi być dostępna w czasie wykonywania, do aplikacji połączonych z MSVCRT. lib.|
|**/MDd**|Definiuje `_DEBUG` , `_MT` i `_DLL` i powoduje, że aplikacja będzie używać debugowania wielowątkowej-specyficznego i specyficznego dla biblioteki DLL dla biblioteki wykonawczej. Powoduje też, że kompilator umieszcza nazwę biblioteki MSVCRTD.lib w pliku .obj.|
|**/MT**|Powoduje, że aplikacja korzysta ze statycznej, wielowątkowej wersji biblioteki wykonawczej. Definiuje `_MT` i powoduje, że kompilator umieszcza nazwę biblioteki libcmt. lib w pliku. obj, tak aby konsolidator używał libcmt. lib do rozpoznawania symboli zewnętrznych.|
|**/MTd**|Definiuje `_DEBUG` i `_MT` . Ta opcja również powoduje, że kompilator umieszcza nazwę biblioteki LIBCMTD.lib w pliku .obj, tak aby konsolidator użył LIBCMTD.lib, aby rozwiązać zewnętrzne symbole.|
|**/LD**|Tworzy DLL.<br /><br /> Przekazuje opcję **/dll** do konsolidatora. Konsolidator szuka, ale nie wymaga `DllMain` funkcji. Jeśli nie napiszesz `DllMain` funkcji, konsolidator wstawia `DllMain` funkcję ZWRACAJĄCĄ wartość true.<br /><br /> Łączy kod uruchamiający biblioteki DLL.<br /><br /> Tworzy bibliotekę importu (.lib), jeżeli nie określono pliku eksportu (.exp) w wierszu polecenia. Bibliotekę importu łączy się z aplikacjami, które wywołują bibliotekę DLL.<br /><br /> Interpretuje [/Fe (Nazwij plik exe)](fe-name-exe-file.md) jako nazwę biblioteki DLL, a nie pliku. exe. Domyślnie nazwa programu otrzymuje nazwę *basename*. dll zamiast *basename*. exe.<br /><br /> Oznacza **/MT** , chyba że jawnie określono **/MD**.|
|**/LDd**|Tworzy DLL przeznaczoną do debugowania. Definiuje `_MT` i `_DEBUG` .|

Aby uzyskać więcej informacji na temat bibliotek środowiska uruchomieniowego C i bibliotek, które są używane podczas kompilowania z [/CLR (kompilacja w środowisku uruchomieniowym języka wspólnego)](clr-common-language-runtime-compilation.md), zobacz [funkcje biblioteki CRT](../../c-runtime-library/crt-library-features.md).

Wszystkie moduły przekazane do danego wywołania konsolidatora muszą zostać skompilowane z tą samą opcją kompilatora biblioteki wykonawczej (**/MD**, **/MT**, **/LD**).

Aby uzyskać więcej informacji o sposobach korzystania z wersji debugowania bibliotek czasu wykonywania, zobacz [Dokumentacja biblioteki wykonawczej C](../../c-runtime-library/c-run-time-library-reference.md).

Aby uzyskać więcej informacji o bibliotekach DLL, zobacz [tworzenie bibliotek DLL C/C++ w programie Visual Studio](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja generowania kodu**C/C++**  >  **Code Generation** .

1. Zmodyfikuj właściwość **biblioteki środowiska uruchomieniowego** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
