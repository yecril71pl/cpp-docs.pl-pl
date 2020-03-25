---
title: Błąd PRJ0050 kompilacji projektu
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: 56e092b5f7c33ad9543951621b2a9d8f6992331f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191993"
---
# <a name="project-build-error-prj0050"></a>Błąd PRJ0050 kompilacji projektu

Nie można zarejestrować danych wyjściowych. Upewnij się, że masz odpowiednie uprawnienia do modyfikowania rejestru.

System kompilacji C++ wizualnej nie mógł zarejestrować danych wyjściowych kompilacji (DLL lub exe). Aby zmodyfikować rejestr, należy zalogować się jako administrator.

Jeśli tworzysz plik. dll, możesz spróbować zarejestrować plik. dll ręcznie przy użyciu programu Regsvr32. exe, aby wyświetlić informacje o tym, dlaczego kompilacja nie powiodła się.

Jeśli nie tworzysz pliku dll, poszukaj w dzienniku kompilacji polecenia, które powoduje błąd.
