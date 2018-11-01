---
title: Zarządzanie biblioteką
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: 69cd03e029d014b9b74a8688f155dfb1f023b55c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477067"
---
# <a name="managing-a-library"></a>Zarządzanie biblioteką

Jest to domyślny tryb LIB do tworzenia lub modyfikowania biblioteki obiektów COFF. Lib — jest uruchamiany w tym trybie, gdy nie zostanie określony/extract (Aby skopiować obiekt do pliku) lub/DEF (do tworzenia biblioteki importowanej).

Aby utworzyć bibliotekę z obiektów i/lub biblioteki, użyj następującej składni:

```
LIB [options...] files...
```

To polecenie tworzy bibliotekę z danych wejściowych co najmniej jeden *pliki*. *Pliki* może być plików obiektu COFF, pliki obiektów OMF 32-bitowych lub istniejących bibliotek COFF. LIB tworzy jedną bibliotekę, która zawiera wszystkie obiekty w określonych plików. Jeśli plik wejściowy jest plikiem obiektów OMF 32-bitowych, LIB przed kompilacją biblioteki konwertuje ją na COFF. Lib — nie można zaakceptować obiekt OMF 32-bitowy, który znajduje się w bibliotece, utworzone przez 16-bitową wersję biblioteki. Należy najpierw użyć LIB 16-bitowych można wyodrębnić obiektu. następnie przy użyciu pliku wyodrębnione obiektu jako dane wejściowe LIB 32-bitowych.

Domyślnie, LIB nazwy pliku wyjściowego przy użyciu podstawowej nazwy pierwszy plik obiektu lub biblioteki i rozszerzenia. lib. Plik wyjściowy jest umieszczany w bieżącym katalogu. Jeśli plik już istnieje o takiej samej nazwie, plik wyjściowy zastępuje istniejący plik. Aby zachować istniejącą bibliotekę, użyj opcji Out, aby określić nazwę dla pliku wyjściowego.

Poniższe opcje są stosowane do tworzenia i modyfikowania biblioteki:

**/ LIBPATH:** *dir*<br/>
Zastępuje ścieżki biblioteki środowiska. Aby uzyskać szczegółowe informacje, zobacz opis łącza [/libpath —](../../build/reference/libpath-additional-libpath.md) opcji.

**/ LIST**<br/>
Wyświetla informacje o bibliotece wyjściowej na wyjście standardowe. Dane wyjściowe mogą zostać przekierowane do pliku. Można użyć/list, aby określić zawartość istniejącej biblioteki bez modyfikowania go.

**/ NAME:** *nazwy pliku*<br/>
Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki dll, dla których jest ona kompilowana biblioteki importu.

**/ NODEFAULTLIB**<br/>
Usuwa co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. Zobacz [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) Aby uzyskać więcej informacji.

**/ OUT:** *nazwy pliku*<br/>
Przesłania domyślną nazwę pliku wyjściowego. Domyślnie dane wyjściowe biblioteki jest tworzony w bieżącym katalogu, o nazwie podstawowej pierwszego pliku biblioteki lub obiekt, w wierszu polecenia i rozszerzenia. lib.

**/ REMOVE:** *obiektu*<br/>
Pomija określony *obiektu* z biblioteki wyjściowej. LIB tworzy bibliotekę wyjściową, łącząc wszystkie obiekty (w plikach obiektu lub biblioteki), a następnie usuwając wszystkie obiekty określone za pomocą/Remove.

**/ SUBSYSTEM:**{**KONSOLI** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM** &AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **NATYWNYCH** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [, #[. ##]]<br/>
Informuje system operacyjny, jak uruchomić program, utworzone przez łączenie z biblioteki wyjściowej. Aby uzyskać więcej informacji, zobacz opis łącza [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji.

Opcje LIB, określone w wierszu polecenia nie jest uwzględniana.

Lib — służy do wykonywania następujących zadań zarządzania biblioteką:

- Aby dodać obiekty do biblioteki, określ nazwę pliku dla istniejącej biblioteki i nazwy plików dla nowych obiektów.

- Aby połączyć bibliotek, określ nazwy plików w bibliotece. Można dodawać obiekty i łączyć biblioteki za pomocą jednego polecenia LIB.

- Aby zastąpić członka biblioteki nowy obiekt, określ bibliotekę zawierającą obiektem Członkowskim, który ma zostać zastąpione i nazwę pliku dla nowego obiektu (lub biblioteki, która ją zawiera). Obiekt, który ma taką samą nazwę w istnieje więcej niż jeden plik wejściowy, LIB umieszcza ostatni obiekt określony w poleceniu LIB w bibliotece wyjściowej. Podczas zastępowania członka biblioteki, pamiętaj określić nowy obiekt lub biblioteki po biblioteki, która zawiera stary obiekt.

- Aby usunąć członka z biblioteki, użyj opcji/Remove. LIB przetwarza wszystkie specyfikacje/Remove po połączeniu wszystkich obiektów danych wejściowych, niezależnie od kolejności wiersza polecenia.

> [!NOTE]
>  Zarówno nie można usunąć element członkowski i Wyodrębnij jego zawartość do pliku, w tym samym kroku. Należy najpierw wyodrębnić obiektu składowego przy użyciu/extract, a następnie uruchom ponownie za pomocą/Remove LIB. To zachowanie różni się od LIB 16-bitowych (dla biblioteki OMF) podany w innych produktów firmy Microsoft.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](../../build/reference/lib-reference.md)