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
ms.openlocfilehash: 0e7fe5ffbb8a6ccdd5ef02d2cf3feb6b94d48233
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|`pathname`|Nazwa i ścieżka pliku wyjściowego utworzonego przez **/P** — opcja kompilatora.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj **/Fi** — opcja kompilatora w połączeniu z **/P** — opcja kompilatora.  
  
 Jeśli określisz tylko ścieżka dla `pathname` parametr, podstawowa nazwa pliku źródłowego jest używany jako podstawowa nazwa pliku wstępnie przetworzonych danych wyjściowych. `pathname` Parametr nie jest wymagane rozszerzenie nazwy pliku określonej. Jednak rozszerzenie ".i" jest używana, jeśli nie określisz rozszerzenie nazwy pliku.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie w wierszu przetwarza wstępnie PROGRAM.cpp, zachowuje komentarze, dodaje [#line](../../preprocessor/hash-line-directive-c-cpp.md) dyrektywy i zapisuje wyniki w pliku MYPROCESS.i.  
  
```  
CL /P /FiMYPROCESS.I PROGRAM.CPP  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md)   
 [Określanie nazwy ścieżki](../../build/reference/specifying-the-pathname.md)