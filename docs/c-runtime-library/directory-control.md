---
title: Kontrola katalogu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- controls [C++], directory
- directory control routines
ms.assetid: a72dcf6f-f366-4d20-8850-0e19cc53ca18
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d29bd8306cdf7bedecfa7f395992a385f182399
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="directory-control"></a>Kontrola katalogu

Te procedury dostępu, modyfikowania i uzyskaj informacje na temat struktury katalogów.

## <a name="directory-control-routines"></a>Procedury kontroli katalogu

|Procedura|Zastosowanie|
|-------------|---------|
|[_chdir, _wchdir](../c-runtime-library/reference/chdir-wchdir.md)|Zmień bieżący katalog roboczy|
|[_chdrive](../c-runtime-library/reference/chdrive.md)|Zmień bieżący dysk|
|[_getcwd, _wgetcwd](../c-runtime-library/reference/getcwd-wgetcwd.md)|Pobierz bieżący katalog roboczy na domyślnym dysku|
|[_getdcwd, _wgetdcwd](../c-runtime-library/reference/getdcwd-wgetdcwd.md)|Pobierz bieżący katalog roboczy dla określonego dysku|
|[_getdiskfree](../c-runtime-library/reference/getdiskfree.md)|Wypełnia **_diskfree_t —** struktury informacji o dysku.|
|[_getdrive](../c-runtime-library/reference/getdrive.md)|Pobierz bieżący dysk (ustawienie domyślne)|
|[_getdrives](../c-runtime-library/reference/getdrives.md)|Zwraca maska bitowa reprezentująca aktualnie dostępnych dysków.|
|[_mkdir, _wmkdir](../c-runtime-library/reference/mkdir-wmkdir.md)|Utwórz nowy katalog|
|[_rmdir, _wrmdir](../c-runtime-library/reference/rmdir-wrmdir.md)|Usuń katalog|
|[_searchenv —, _wsearchenv —](../c-runtime-library/reference/searchenv-wsearchenv.md), [_searchenv_s —, _wsearchenv_s —](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Wyszukaj podany plik na określonych ścieżek|

## <a name="see-also"></a>Zobacz też

[Universal C procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [Obsługa plików](../c-runtime-library/file-handling.md)<br/>
 [Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
