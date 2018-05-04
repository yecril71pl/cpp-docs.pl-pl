---
title: Wybieranie formatu modułu .netmodule pliki wejściowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62575d3e816bdc10587e7a4c9cebcea735329ec1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Wybieranie formatu plików wejściowych .netmodule
Plik .obj MSIL (skompilowane z [/CLR](../../build/reference/clr-common-language-runtime-compilation.md)) może również służyć jako plik modułu .netmodule.  pliki .obj zawierają metadanych i symboli natywnych.  modułów .netmodule zawierają tylko metadane.  
  
 Można przekazać plik .obj MSIL do innych kompilatora Visual Studio za pomocą/addmodule — opcja kompilatora (ale należy pamiętać, że plik .obj staje się częścią zestawu wynikowego i muszą być dostarczone z zestawu).  Na przykład Visual C# i Visual Basic ma/addmodule — opcja kompilatora.  
  
> [!NOTE]
>  W większości przypadków należy przekazać do konsolidatora plik .obj z kompilacji, która utworzony moduł .net.  Przekazywanie pliku modułu DLL lub moduł .netmodule MSIL do konsolidatora może spowodować LNK1107.  
  
 pliki .obj, wraz z ich pliki .h skojarzone, które odwołują się za pośrednictwem #include w źródle, umożliwiają aplikacjom C++ korzystać z natywnych typów w module, podczas gdy w pliku modułu .netmodule tylko typy zarządzane mogą być używane przez aplikację języka C++.  Przy próbie przekazania pliku .obj do #using, informacje o typach natywnych nie będą dostępne; # plik .h pliku obj. include zamiast tego.  
  
 Inne kompilatory Visual Studio może używać tylko typy zarządzane z modułu.  
  
 Aby określić, czy należy użyć modułu .netmodule lub plik obj jako danych wejściowych modułu do konsolidatora Visual C++, skorzystaj z następujących:  
  
-   Jeśli tworzysz kompilatora Visual Studio, inne niż Visual C++, tworzy modułu .netmodule i użyć modułu .netmodule jako dane wejściowe konsolidatora.  
  
-   Jeśli używasz kompilatora Visual C++ do tworzenia modułów i jeśli moduły będą służyć do tworzenia inną niż bibliotekę, użyj plików .obj produkowane przez kompilator jako danych wejściowych modułu do konsolidatora; nie należy używać pliku modułu .netmodule jako dane wejściowe.  
  
-   Jeśli moduły będą używane do tworzenia biblioteki native (nie zarządzanego), użyj pliki obj jako dane wejściowe modułu konsolidator i Generuj plik biblioteki lib.  
  
-   Jeśli moduły będą używane do tworzenia zarządzanej biblioteki, a wszystkie dane wejściowe modułu konsolidator będzie możliwe do zweryfikowania (realizowane z/CLR: Safe), użyj pliki obj jako dane wejściowe modułu konsolidator i generowanie dll (assembly) lub plik biblioteki modułu .netmodule (modułu).  
  
-   Jeśli moduły będą służyć do tworzenia zarządzanej biblioteki i co najmniej jeden modułów dane wejściowe konsolidatora zostaną zwrócone z tylko/CLR, użyj pliki obj jako dane wejściowe modułu konsolidator i generowanie dll (assembly).  Jeśli chcesz udostępnić typy zarządzane z biblioteki i czy ma aplikacjom korzystać z natywnych typów w bibliotece C++, biblioteki będzie zawierał pliki .obj dla modułów składowych bibliotek (również można wysłać pliki .h dla każdego modułu Dlatego może być przywoływany z #include z kodu źródłowego).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki .netmodule — wejście konsolidatora](../../build/reference/netmodule-files-as-linker-input.md)