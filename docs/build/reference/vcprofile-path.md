---
title: VCPROFILE_PATH | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VCPROFILE_PATH
dev_langs: C++
helpviewer_keywords: VCPROFILE_PATH environment variable
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d5b4a2bbb46e906883f3f0c99c84d3b12cc0f104
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vcprofilepath"></a>VCPROFILE_PATH
Określ katalog, aby utworzyć pliki .pgc.  
  
## <a name="syntax"></a>Składnia  
  
```  
VCPROFILE_PATH=path  
```  
  
#### <a name="parameters"></a>Parametry  
 `path`  
 Ścieżka katalogu, w którym .pgc pliki zostaną dodane.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie pliki .pgc są tworzone w tym samym katalogu co plik binarny PROFILOWANEGO.  Jednak jeśli ścieżka bezwzględna plik binarny nie istnieje, jak może to miejsce podczas uruchamiania scenariuszy profilu na innym komputerze, z którym został utworzony plik binarny, możesz ustawić `VCPROFILE_PATH` do ścieżki, która istnieje.  
  
## <a name="example"></a>Przykład  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe dla optymalizacji sterowanych profilem](../../build/reference/environment-variables-for-profile-guided-optimizations.md)