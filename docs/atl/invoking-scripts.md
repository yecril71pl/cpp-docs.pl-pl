---
title: Wywoływanie skryptów (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- StringRegister
dev_langs:
- C++
helpviewer_keywords:
- StringRegister method
- scripts, invoking registry in ATL
ms.assetid: eabd41ee-586b-4266-9e92-5aaad04b73a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 91d11b86b2b7cf17ef90ab701b06c6f31b272691
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="invoking-scripts"></a>Skrypty wywołania
[Przy użyciu parametry wymienne (Rejestrator preprocesora)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) omówiono mapy zastąpienia i uwagi metody rejestratora **AddReplacement**. Rejestrator ma osiem innych metod specyficzne dla skryptów, a wszystkie są opisane w poniższej tabeli.  
  
|Metoda|Składnia/opis|  
|------------|-------------------------|  
|**ResourceRegister**|**HRESULT ResourceRegister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Rejestruje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. `nID` i `szType` odpowiednio zawierają identyfikator i typu zasobu.|  
|**ResourceUnregister**|**HRESULT ResourceUnregister (LPCOLESTR***resFileName* **, UINT** `nID` **, LPCOLESTR** `szType` **);** <br /><br /> Wyrejestrowuje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. `nID` i `szType` odpowiednio zawierają identyfikator i typu zasobu.|  
|**ResourceRegisterSz**|**HRESULT ResourceRegisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Rejestruje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. *szID* i `szType` zawierają odpowiednio identyfikator ciągu i typu zasobu.|  
|**ResourceUnregisterSz**|**HRESULT ResourceUnregisterSz (LPCOLESTR***resFileName* **, LPCOLESTR***szID* **, LPCOLESTR** `szType` **);** <br /><br /> Wyrejestrowuje zawarte w module zasobu skryptu. *resFileName* wskazuje ścieżkę UNC do modułu, do samej siebie. *szID* i `szType` zawierają odpowiednio identyfikator ciągu i typu zasobu.|  
|**FileRegister**|**HRESULT FileRegister (LPCOLESTR***fileName***);** <br /><br /> Rejestruje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jej) skryptu zasobu.|  
|**FileUnregister**|**HRESULT FileUnregister (LPCOLESTR***fileName***);** <br /><br /> Wyrejestrowuje skryptu w pliku. *Nazwa pliku* jest ścieżką UNC do pliku, który zawiera (lub jej) skryptu zasobu.|  
|**StringRegister**|**HRESULT StringRegister (LPCOLESTR***danych***);** <br /><br /> Rejestruje skrypt w ciągu. *dane* zawiera sam skrypt.|  
|**StringUnregister**|**HRESULT StringUnregister (LPCOLESTR***danych***);** <br /><br /> Wyrejestrowuje skryptu w ciągu. *dane* zawiera sam skrypt.|  
  
 **ResourceRegisterSz** i **ResourceUnregisterSz**, są podobne do **ResourceRegister** i **ResourceUnregister**, ale pozwala na określenie ciągu Identyfikator.  
  
 Metody **FileRegister** i **FileUnregister** są przydatne, jeśli nie chcesz, aby skrypt w zasobie lub jeśli użytkownik chce skryptu w pliku. Metody **StringRegister** i **StringUnregister** pliku .rgs mają być przechowywane w ciągu dynamicznie przydzielonego dozwolonych.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie skryptów rejestratora](../atl/creating-registrar-scripts.md)

