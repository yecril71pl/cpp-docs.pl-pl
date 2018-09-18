---
title: Niskiego poziomu operacji We/Wy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d263d1d61a6dcc6921d6918db2b89386e918551
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018317"
---
# <a name="low-level-io"></a>We/Wy niskiego poziomu

Te wywołają procedurę obsługi systemu operacyjnego bezpośrednio do operacji niższe niż te dostarczone przez strumień we/wy. Niskiego poziomu dane wejściowe i wyjściowe wywołania wykonaj nie buforu lub formatu danych.

Procedur niższego poziomu mogą uzyskiwać dostęp standardowych strumieni otwierane w momencie uruchamiania programu przy użyciu następujących wstępnie zdefiniowanych deskryptory.

|Strumień|Deskryptor pliku|
|------------|---------------------|
|**stdin**|0|
|**STDOUT**|1|
|**strumienia wyjściowego stderr**|2|

Zestaw operacji We/Wy niskiego poziomu w procedury [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) zmienną globalną, po wystąpieniu błędu. Musi zawierać stdio —. H, gdy używasz funkcji niskiego poziomu, tylko wtedy, gdy program wymaga stałą, która jest zdefiniowana w stdio —. Godz., takie jak wskaźnik końca pliku (**EOF**).

## <a name="low-level-io-functions"></a>Funkcje niskiego poziomu we/wy

|Funkcja|Zastosowanie|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Zamknij plik|
|[_commit](../c-runtime-library/reference/commit.md)|Opróżnij plik na dysku|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Utwórz plik|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|Zwracany następny dostępny deskryptor pliku dla danego pliku|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Utwórz deskryptor drugiego dla danego pliku|
|[_eof](../c-runtime-library/reference/eof.md)|Test końca pliku|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Zmiana położenia pliku wskaźnik do podanej lokalizacji|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Otwórz plik|
|[_read](../c-runtime-library/reference/read.md)|Odczyt danych z pliku|
|[_sopen, _wsopen —](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s —, _wsopen_s —](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Otwórz plik do udostępniania plików|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Pobierz bieżącą pozycję wskaźnika pliku|
|[_umask —](../c-runtime-library/reference/umask.md), [_umask_s —](../c-runtime-library/reference/umask-s.md)|Ustaw uprawnienia pliku maski|
|[_write](../c-runtime-library/reference/write.md)|Zapisuje dane pliku|

 **_dup —** i **_dup2 —** są zwykle używane do kojarzenia deskryptorów plików wstępnie zdefiniowane z różnych plików.

## <a name="see-also"></a>Zobacz też

[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Wywołania systemowe](../c-runtime-library/system-calls.md)<br/>
