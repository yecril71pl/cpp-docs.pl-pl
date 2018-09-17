---
title: -Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Fi
dev_langs:
- C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfe9e54dbafbcbd27763060dc9d81b21bac2503d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709406"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego)

Określa nazwę pliku wyjściowego, do którego [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) — opcja kompilatora zapisuje wstępnie przetworzone produkty wyjściowe.

## <a name="syntax"></a>Składnia

```
/Fipathname
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pathname`|Nazwa i ścieżka pliku wyjściowego produkowane przez **/P** — opcja kompilatora.|

## <a name="remarks"></a>Uwagi

Użyj **/Fi** — opcja kompilatora w połączeniu z **/P** — opcja kompilatora.

Jeśli określisz tylko ścieżka dla `pathname` parametru podstawowej nazwy pliku źródłowego jest używana jako nazwa podstawowa pliku wstępnie przetworzone produkty wyjściowe. `pathname` Parametr nie jest wymagane rozszerzenie nazwy pliku określonej. Jednak rozszerzenie ".i" jest używana, jeśli nie określisz rozszerzenie nazwy pliku.

## <a name="example"></a>Przykład

Następujące polecenie w wierszu wstępnie przetwarza PROGRAM.cpp, zachowuje komentarze, dodaje [#line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektyw i zapisuje wynik w pliku MYPROCESS.i.

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md)
[Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)