---
title: raw_dispinterfaces — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 73c58b72b27de8dcf96e8ab9464d0fb6bce12b66
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216225"
---
# <a name="raw_dispinterfaces-import-attribute"></a>raw_dispinterfaces — atrybut importowania

**C++Specjalne**

Instruuje kompilator, aby generował funkcje otoki niskiego poziomu dla metod dispinterface oraz dla właściwości, `IDispatch::Invoke` które wywołują i zwracają kod błędu HRESULT.

## <a name="syntax"></a>Składnia

> **#import** *Biblioteka typów* **raw_dispinterfaces**

## <a name="remarks"></a>Uwagi

Jeśli ten atrybut nie jest określony, generowane są tylko otoki wysokiego poziomu, które generują C++ wyjątki w przypadku niepowodzenia.

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
