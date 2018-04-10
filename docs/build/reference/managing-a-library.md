---
title: Zarządzanie biblioteką | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 05ced49a960aea0b32365b80fe76095893f63d5e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="managing-a-library"></a>Zarządzanie biblioteką
Jest to domyślny tryb dla LIB do tworzenia lub modyfikowania biblioteki obiektów COFF. LIB działa w tym trybie, jeśli nie określisz/extract (Aby skopiować obiekt do pliku) lub/DEF (do tworzenia biblioteki importowanej).  
  
 Aby utworzyć biblioteki z obiektów i/lub biblioteki, użyj następującej składni:  
  
```  
LIB [options...] files...  
```  
  
 To polecenie tworzy bibliotekę z co najmniej jednego wejścia *pliki*. *Pliki* może być obiektu COFF, pliki, pliki obiektów OMF 32-bitowej lub istniejące bibliotekami COFF. LIB tworzy jedną bibliotekę, która zawiera wszystkie obiekty w określonych plików. Jeśli plik wejściowy jest 32-bitowego pliku obiektów OMF, LIB przed zbudowaniem biblioteki konwertuje ją na COFF. Biblioteka nie może zaakceptować obiekt OMF 32-bitowy, który znajduje się w bibliotece utworzone przez 16-bitowej wersji LIB. Należy najpierw użyć LIB 16-bitowych można wyodrębnić obiektu. następnie można użyć obiektu wyodrębnionego pliku jako dane wejściowe LIB 32-bitowych.  
  
 Domyślnie LIB nazwy pliku wyjściowego przy użyciu nazwy podstawowej pierwszy plik obiektu lub biblioteki i rozszerzenia. lib. Plik wyjściowy jest umieszczany w bieżącym katalogu. Jeśli plik już istnieje o takiej samej nazwie, plik wyjściowy zastępuje istniejący plik. Aby zachować istniejącej biblioteki, użyj opcja/out, aby określić nazwę pliku wyjściowego.  
  
 Następujące opcje są stosowane do tworzenia i modyfikowania biblioteki:  
  
 / LIBPATH:`dir`  
 Powoduje zastąpienie środowiska ścieżki biblioteki. Aby uzyskać więcej informacji, zobacz opis łącza [/libpath](../../build/reference/libpath-additional-libpath.md) opcji.  
  
 / LIST  
 Wyświetla informacje o bibliotece wyjściowej na wyjście standardowe. Mogą zostać przekierowane dane wyjściowe do pliku. / List można użyć, aby określić zawartość istniejącej biblioteki bez modyfikowania jej.  
  
 / NAME: *filename*  
 Podczas kompilowania biblioteki importowanej, określa nazwę biblioteki dll, dla której jest tworzona biblioteki importu.  
  
 / NODEFAULTLIB  
 Usuwa co najmniej jedną domyślną bibliotekę z listy bibliotek przeszukiwanych podczas rozpoznawania odwołań zewnętrznych. Zobacz [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) Aby uzyskać więcej informacji.  
  
 / OUT: *filename*  
 Przesłania domyślną nazwę pliku wyjściowego. Domyślnie dane wyjściowe biblioteki jest tworzony w bieżącym katalogu o nazwie podstawowej pierwszego pliku biblioteki lub obiekt w wierszu polecenia i rozszerzenia. lib.  
  
 / REMOVE: *obiektu*  
 Pomija określony *obiektu* z biblioteki wyjściowej. LIB tworzy bibliotekę wyjściową, łącząc wszystkie obiekty (zarówno w plikach obiektu lub biblioteki), a następnie usuwając wszystkie obiekty określone za pomocą/Remove.  
  
 / SUBSYSTEM: {KONSOLI &#124; EFI_APPLICATION &#124; EFI_BOOT_SERVICE_DRIVER &#124; EFI_ROM &#124; EFI_RUNTIME_DRIVER &#124; NATYWNY &#124; POSIX &#124; WINDOWS &#124; WINDOWSCE} [, #[. ##]]  
 Informuje system operacyjny, jak uruchomić program utworzony przez łączenie z biblioteki wyjściowej. Aby uzyskać więcej informacji, zobacz opis łącza [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opcji.  
  
 Opcje LIB określona w wierszu polecenia nie jest uwzględniana.  
  
 LIB umożliwia wykonywanie następujących zadań zarządzania biblioteką:  
  
-   Aby dodać obiekty do biblioteki, określ nazwę pliku dla istniejącej biblioteki i nazwy plików dla nowych obiektów.  
  
-   Aby połączyć bibliotek, określ nazwy pliku biblioteki. Można dodawać obiektów i łączenie biblioteki za pomocą jednego polecenia LIB.  
  
-   Aby zastąpić członka biblioteki nowy obiekt, określ bibliotekę zawierającą obiektu elementu członkowskiego do wymiany i nazwę pliku dla nowego obiektu (lub biblioteki, która go zawiera). Gdy obiekt, który ma taką samą nazwę w więcej niż jeden plik wejściowy, LIB umieszcza ostatni obiekt określony w poleceniu LIB w bibliotece wyjściowej. Podczas zastępowania członka biblioteki należy określić nowy obiekt lub biblioteki po biblioteki, który zawiera stary obiekt.  
  
-   Aby usunąć element członkowski z biblioteki, użyj opcji/Remove. LIB przetwarza dowolnego specyfikacjach/Remove po połączeniu wszystkie obiekty wejściowe, niezależnie od kolejności wiersza polecenia.  
  
> [!NOTE]
>  Jednocześnie nie można usunąć element członkowski i wyodrębnij go do pliku w tym samym kroku. Należy najpierw wyodrębnić obiektu elementu członkowskiego przy użyciu/extract, a następnie uruchom ponownie za pomocą/Remove LIB. To zachowanie różni się od LIB 16-bitowych (dla biblioteki OMF) dostępnych w innych produktów firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz też  
 [LIB — dokumentacja](../../build/reference/lib-reference.md)