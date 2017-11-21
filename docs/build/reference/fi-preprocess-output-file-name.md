---
title: "-Fi (Przetwarzaj wstępnie nazwę pliku wyjściowego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Fi
dev_langs: C++
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a6499e3720cf6d61fa124c2fc5a43ce2ff30f249
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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