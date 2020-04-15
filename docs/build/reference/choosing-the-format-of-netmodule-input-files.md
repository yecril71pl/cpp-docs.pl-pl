---
title: Wybieranie formatu plików wejściowych .netmodule
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320574"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Wybieranie formatu plików wejściowych .netmodule

Plik MSIL .obj (skompilowany z [/clr)](clr-common-language-runtime-compilation.md)może być również używany jako plik .netmodule.  Pliki obj zawierają metadane i symbole macierzyste.  .netmodules zawierają tylko metadane.

Plik MSIL .obj można przekazać do dowolnego innego kompilatora programu Visual Studio za pośrednictwem opcji kompilatora /addmodule (ale należy pamiętać, że plik obj staje się częścią wynikowego zestawu i musi być dostarczany z zestawem).  Na przykład Visual C# i Visual Basic mają opcję kompilatora /addmodule.

> [!NOTE]
> W większości przypadków należy przekazać do konsolidatora plik obj z kompilacji, która utworzyła moduł .net.  Przekazanie pliku modułu .dll lub .netmodule MSIL do konsolidatora może spowodować LNK1107.

.obj plików, wraz z ich skojarzonych .h plików, do których odwołujesz się za pośrednictwem #include w źródle, umożliwiają aplikacjom Języka C++ korzystanie z typów macierzystych w module, podczas gdy w pliku .netmodule tylko typy zarządzane mogą być używane przez aplikację C++.  Jeśli spróbujesz przekazać plik obj do #using, informacje o typach natywnych nie będą dostępne; #include pliku .obj .h.

Inne kompilatory programu Visual Studio mogą korzystać tylko z typów zarządzanych z modułu.

Aby ustalić, czy należy użyć pliku .netmodule, czy pliku obj jako wejścia modułu do konsolidatora MSVC, należy użyć pliku .netmodule lub obj:

- Jeśli tworzysz za pomocą kompilatora programu Visual Studio innych niż Visual C++, wyprodukuj .netmodule i użyj .netmodule jako dane wejściowe do konsolidatora.

- Jeśli używasz kompilatora MSVC do tworzenia modułów i jeśli moduły będą używane do tworzenia czegoś innego niż biblioteka, użyj plików obj wyprodukowanych przez kompilator jako dane wejściowe modułu do konsolidatora; nie używaj pliku .netmodule jako danych wejściowych.

- Jeśli moduły będą używane do tworzenia natywnej (nie zarządzanej) biblioteki, użyj plików obj jako danych wejściowych modułu do konsolidatora i wygeneruj plik biblioteki .lib.

- Jeśli moduły będą używane do tworzenia biblioteki zarządzanej, a wszystkie dane wejściowe modułu do konsolidatora będą weryfikowalne (produkowane za pomocą /clr:safe), użyj plików .obj jako wejścia modułu do konsolidatora i wygeneruj plik biblioteki .dll (assembly) lub .netmodule (moduł).

- Jeśli moduły będą używane do tworzenia biblioteki zarządzanej, a jeśli jeden lub więcej modułów wejściowych do konsolidatora będą produkowane z tylko /clr, użyj .obj plików jako wejście modułu do konsolidatora i wygenerować .dll (zestaw).  Jeśli chcesz udostępnić typy zarządzane z biblioteki i jeśli chcesz również, aby aplikacje języka C++ wykorzystywały typy macierzyste w bibliotece, biblioteka będzie składać się z plików obj dla modułów składników bibliotek (należy również wysłać pliki .h dla każdego modułu, aby można było odwoływać się do nich z #include z kodu źródłowego).

## <a name="see-also"></a>Zobacz też

[Pliki .netmodule — wejście konsolidatora](netmodule-files-as-linker-input.md)
