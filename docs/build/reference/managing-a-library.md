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
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336407"
---
# <a name="managing-a-library"></a>Zarządzanie biblioteką

Domyślnym trybem lib jest tworzenie lub modyfikowanie biblioteki obiektów COFF. LIB działa w tym trybie, gdy nie określisz /EXTRACT (skopiować obiekt do pliku) lub /DEF (aby utworzyć bibliotekę importu).

Aby utworzyć bibliotekę z obiektów i/lub bibliotek, należy użyć następującej składni:

```
LIB [options...] files...
```

To polecenie tworzy bibliotekę z jednego lub kilku *plików*wejściowych . *Pliki* mogą być plikami obiektów COFF, 32-bitowymi plikami obiektów OMF lub istniejącymi bibliotekami COFF. LIB tworzy jedną bibliotekę zawierającą wszystkie obiekty w określonych plikach. Jeśli plik wejściowy jest 32-bitowym plikiem obiektu OMF, LIB konwertuje go na COFF przed zbudowaniem biblioteki. LIB nie może zaakceptować 32-bitowego obiektu OMF, który znajduje się w bibliotece utworzonej przez 16-bitową wersję lib. Aby wyodrębnić obiekt, należy najpierw użyć 16-bitowej biblioteki LIB; następnie można użyć wyodrębnionego pliku obiektu jako danych wejściowych do 32-bitowej biblioteki LIB.

Domyślnie LIB nazywa plik wyjściowy przy użyciu nazwy podstawowej pierwszego pliku obiektu lub biblioteki oraz rozszerzenia .lib. Plik wyjściowy jest umieszczany w bieżącym katalogu. Jeśli plik już istnieje o tej samej nazwie, plik wyjściowy zastępuje istniejący plik. Aby zachować istniejącą bibliotekę, użyj opcji /OUT, aby określić nazwę pliku wyjściowego.

Następujące opcje dotyczą tworzenia i modyfikowania biblioteki:

**/LIBPATH:** *reż.*<br/>
Zastępuje ścieżkę biblioteki środowiska. Szczegółowe informacje można znaleźć w opisie opcji LINK [/LIBPATH.](libpath-additional-libpath.md)

**/LISTA**<br/>
Wyświetla informacje o bibliotece danych wyjściowych na standardowe dane wyjściowe. Dane wyjściowe można przekierować do pliku. Można użyć /LIST, aby określić zawartość istniejącej biblioteki bez modyfikowania go.

**/NAME:** *nazwa pliku*<br/>
Podczas tworzenia biblioteki importu określa nazwę biblioteki DLL, dla której jest budowana biblioteka importu.

**/NODEFAULTLIB**<br/>
Usuwa jedną lub więcej bibliotek domyślnych z listy bibliotek, które wyszukuje podczas rozpoznawania odwołań zewnętrznych. Zobacz [/NODEFAULTLIB aby](nodefaultlib-ignore-libraries.md) uzyskać więcej informacji.

**/OUT:** *nazwa pliku*<br/>
Zastępuje domyślną wyjściową nazwę pliku. Domyślnie biblioteka danych wyjściowych jest tworzona w bieżącym katalogu, z nazwą podstawową pierwszej biblioteki lub pliku obiektu w wierszu polecenia i rozszerzeniem .lib.

**/REMOVE:** *obiekt*<br/>
Pomija określony *obiekt* z biblioteki danych wyjściowych. LIB tworzy bibliotekę danych wyjściowych, łącząc wszystkie obiekty (w plikach obiektów lub bibliotekach), a następnie usuwając wszystkie obiekty określone za pomocą /REMOVE.

**/SUBSYSTEM:**{ &#124; **EFI_APPLICATION** **EFI_APPLICATION &#124;** EFI_BOOT_SERVICE_DRIVER **&#124;** &#124; EFI_ROM EFI_ROM &#124; **EFI_ROM** **EFI_RUNTIME_DRIVER &#124;** &#124; **POSIX** &#124; **NATIVE** WINDOWS &#124; **WINDOWSCE** }[,#[.##]] **WINDOWSCE**<br/>
Informuje system operacyjny, jak uruchomić program utworzony przez połączenie z biblioteką danych wyjściowych. Aby uzyskać więcej informacji, zobacz opis opcji [ŁĄCZE /PODSYSTEM.](subsystem-specify-subsystem.md)

W opcjach LIB określonych w wierszu polecenia nie jest rozróżniana wielkość liter.

Za pomocą biblioteki LIB można wykonywać następujące zadania związane z zarządzaniem biblioteką:

- Aby dodać obiekty do biblioteki, określ nazwę pliku istniejącej biblioteki i nazwy plików dla nowych obiektów.

- Aby połączyć biblioteki, określ nazwy plików biblioteki. Można dodawać obiekty i łączyć biblioteki za pomocą jednego polecenia LIB.

- Aby zastąpić członka biblioteki nowym obiektem, określ bibliotekę zawierającą obiekt członkowski, który ma zostać zastąpiony, oraz nazwę pliku nowego obiektu (lub biblioteki, która go zawiera). Jeśli obiekt o tej samej nazwie istnieje w więcej niż jednym pliku wejściowym, lib umieszcza ostatni obiekt określony w poleceniu LIB w bibliotece wyjściowej. Podczas zastępowania elementu członkowskiego biblioteki należy określić nowy obiekt lub bibliotekę po bibliotece zawierającej stary obiekt.

- Aby usunąć członka z biblioteki, użyj opcji /REMOVE. LIB przetwarza wszelkie specyfikacje /REMOVE po połączeniu wszystkich obiektów wejściowych, niezależnie od kolejności wiersza polecenia.

> [!NOTE]
> Nie można zarówno usunąć członka i wyodrębnić go do pliku w tym samym kroku. Najpierw należy wyodrębnić obiekt elementu członkowskiego przy użyciu /EXTRACT, a następnie ponownie uruchomić LIB za pomocą /REMOVE. To zachowanie różni się od 16-bitowej biblioteki LIB (dla bibliotek OMF) dostępnej w innych produktach firmy Microsoft.

## <a name="see-also"></a>Zobacz też

[LIB — dokumentacja](lib-reference.md)
