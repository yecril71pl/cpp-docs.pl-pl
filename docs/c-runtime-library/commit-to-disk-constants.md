---
title: Stałe typu Commit-Disk | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- vc.constants
dev_langs:
- C++
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c3a815948c127c5dec0fe6412ab3c358aa409e2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391067"
---
# <a name="commit-to-disk-constants"></a>Stałe typu commit-to-disk
**Microsoft Specific**  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Uwagi  
 Te stałe specyficzne dla firmy Microsoft umożliwia określenie, czy skojarzony z otwartego pliku wysłaniem do buforów systemu operacyjnego lub na dysku. Tryb jest uwzględniona w parametrach określenie typu dostępu odczytu i zapisu (**"r"**, **"w"**, **""**, **"r +"**, **"w +"** , **"+"**).  
  
 Tryby commit-to-disk są następujące:  
  
 **c**  
 Zapisuje zawartość niezapisanych określonego bufora na dysku. Ta funkcja commit-to-disk jest wykonywana wyłącznie w jawnego wywołania albo [fflush —](../c-runtime-library/reference/fflush.md) lub [_flushall —](../c-runtime-library/reference/flushall.md) funkcji. Ten tryb jest przydatny podczas pracy z danymi poufnymi. Na przykład, jeśli program kończy się po wywołaniu `fflush` lub `_flushall`, można zapewnić, że osiągnięcie systemu operacyjnego buforów danych. Jednak jeśli plik jest otwarty z **c** opcji danych może nigdy nie była na dysku, jeśli system operacyjny również zakończy się.  
  
 **N**  
 Zapisuje zawartość niezapisanych określonego bufora do buforów systemu operacyjnego. System operacyjny może dane z pamięci podręcznej, a następnie określenie optymalny czas zapisu na dysku. W warunkach wiele to zachowanie sprawia, że program wydajne zachowania. Jednak w przypadku przechowywania danych krytyczne (np. transakcje bank lub informacje o bilecie linii lotniczych) należy rozważyć użycie **c** opcji. **n** tryb jest ustawieniem domyślnym.  
  
> [!NOTE]
>  **c** i **n** opcje nie są częścią standardu ANSI `fopen`, ale są rozszerzenia Microsoft i nie powinna być używana których przenośność ANSI jest potrzebne.  
  
## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Za pomocą funkcji Commit-to-Disk z istniejącego kodu  
 Domyślnie wywołań [fflush —](../c-runtime-library/reference/fflush.md) lub [_flushall —](../c-runtime-library/reference/flushall.md) funkcji biblioteki zapisu danych do buforów obsługiwanego przez system operacyjny. System operacyjny określa czas optymalne rzeczywistości zapisać danych na dysku. Funkcja commit-to-disk biblioteki wykonawczej umożliwia upewnij się, że krytyczne dane są zapisywane bezpośrednio na dysku, a nie do buforów systemu operacyjnego. Tej funkcji można przydzielić do istniejącego programu bez ponowne zapisanie go przez łączenie z jego plików obiektów z COMMODE.OBJ.  
  
 W wynikowym pliku wykonywalnego, wywołań `fflush` zapisywanie zawartości buforu bezpośrednio do dysku i wywołania `_flushall` zapisać zawartość buforów wszystkich na dysku. Te dwie funkcje są jedynymi osobami wpływ COMMODE.OBJ.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [We/Wy strumienia](../c-runtime-library/stream-i-o.md)   
 [_fdopen —, _wfdopen —](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen —, _wfopen —](../c-runtime-library/reference/fopen-wfopen.md)   
 [Stałe globalne](../c-runtime-library/global-constants.md)