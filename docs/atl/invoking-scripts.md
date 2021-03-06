---
title: Wywoływanie skryptów (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
ms.openlocfilehash: 6ca744ced53677550e7b77f44d4f6550da744372
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62250470"
---
# <a name="invoking-scripts"></a>Wywoływanie skryptów

[Używanie wymiennych parametrów (Preprocesor rejestratora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) w tym artykule omówiono mapy zastąpienia i wymienia metoda rejestratora **AddReplacement**. Rejestrator ma osiem innych metod specyficzne dla skryptów i wszystkie są opisane w poniższej tabeli.

|Metoda|Składnia/opis|
|------------|-------------------------|
|**ResourceRegister**|**HRESULT ResourceRegister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Rejestruje skryptów znajdujących się w zasobie modułu. *resFileName* wskazuje ścieżkę UNC do samego modułu. *nID* i *szType* zawierają odpowiednio identyfikator i typu zasobu.|
|**ResourceUnregister**|**HRESULT ResourceUnregister( LPCOLESTR**  *resFileName* **, UINT**  `nID` **, LPCOLESTR**  `szType` **);**<br /><br /> Wyrejestrowuje skryptów znajdujących się w zasobie modułu. *resFileName* wskazuje ścieżkę UNC do samego modułu. *nID* i *szType* zawierają odpowiednio identyfikator i typu zasobu.|
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Rejestruje skryptów znajdujących się w zasobie modułu. *resFileName* wskazuje ścieżkę UNC do samego modułu. *szID* i *szType* zawierają odpowiednio identyfikator ciągu i typu zasobu.|
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz( LPCOLESTR**  *resFileName* **, LPCOLESTR**  *szID* **, LPCOLESTR**  `szType` **);**<br /><br /> Wyrejestrowuje skryptów znajdujących się w zasobie modułu. *resFileName* wskazuje ścieżkę UNC do samego modułu. *szID* i *szType* zawierają odpowiednio identyfikator ciągu i typu zasobu.|
|**FileRegister**|**HRESULT FileRegister( LPCOLESTR**  *fileName*  **);**<br /><br /> Rejestruje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jest) skrypt zasobu.|
|**FileUnregister**|**HRESULT FileUnregister( LPCOLESTR**  *fileName*  **);**<br /><br /> Wyrejestrowuje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jest) skrypt zasobu.|
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***danych***);**<br /><br /> Rejestruje skryptu w ciągu. *dane* zawiera sam skrypt.|
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***danych***);**<br /><br /> Wyrejestrowuje skryptu w ciągu. *dane* zawiera sam skrypt.|

**ResourceRegisterSz** i **ResourceUnregisterSz**, są podobne do **ResourceRegister** i **ResourceUnregister**, ale istnieje możliwość określenia ciągu Identyfikator.

Metody **FileRegister** i **FileUnregister** są przydatne, jeśli chcesz, aby skrypt w zasobie lub jeśli chcesz, aby skrypt w jej własnym pliku. Metody **StringRegister** i **StringUnregister** pliku .rgs mają być przechowywane w ciągu przydzielany dynamicznie dozwolonych.

## <a name="see-also"></a>Zobacz także

[Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)
