---
title: Modele wątkowości i klasy sekcji krytycznych (ATL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
f1_keywords:
- vc.atl.threads.models
dev_langs:
- C++
helpviewer_keywords:
- ATL, critical sections
- ATL, multithreading
- threading [ATL], models
- critical sections
ms.assetid: 759f05ef-6285-4be6-a2cc-78572dd75146
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b87fdac5220ede47f1acf19088e952fde408a413
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755960"
---
# <a name="threading-models-and-critical-sections-classes"></a>Modele wątkowości i klasy sekcji krytycznych

Poniższe klasy definiują wątkowości modelu i sekcję krytyczną:

- [CAtlAutoThreadModule](../atl/reference/catlautothreadmodule-class.md) implementuje serwer COM wątków w puli, model przedziału.

- [CAtlAutoThreadModuleT](../atl/reference/catlautothreadmodulet-class.md) udostępnia metody wykonywania wątków w puli, modelu typu apartment serwer COM.

- [CComMultiThreadModel](../atl/reference/ccommultithreadmodel-class.md) zapewnia metody obsługujące wielowątkowość zwiększanie i zmniejszanie zmienną. Zawiera sekcję krytyczną.

- [CComMultiThreadModelNoCS](../atl/reference/ccommultithreadmodelnocs-class.md) zapewnia metody obsługujące wielowątkowość zwiększanie i zmniejszanie zmienną. Nie zapewnia sekcję krytyczną.

- [CComSingleThreadModel](../atl/reference/ccomsinglethreadmodel-class.md) zawiera metody służące do zwiększanie i zmniejszanie zmienną. Nie zapewnia sekcję krytyczną.

- [CComObjectThreadModel](../atl/reference/atl-typedefs.md#ccomobjectthreadmodel) określa odpowiedniej klasy model wątkowości dla pojedynczego obiektu klasy.

- [CComGlobalsThreadModel](../atl/reference/atl-typedefs.md#ccomglobalsthreadmodel) określa odpowiedniej klasy model wątkowości dla obiektu, który jest ogólnie dostępna.

- [CComAutoCriticalSection](../atl/reference/ccomautocriticalsection-class.md) zawiera metody uzyskiwania i zwalniania sekcję krytyczną. Sekcję krytyczną jest inicjowana automatycznie.

- [CComCriticalSection](../atl/reference/ccomcriticalsection-class.md) zawiera metody uzyskiwania i zwalniania sekcję krytyczną. Można jawnie zainicjować sekcję krytyczną.

- [CComFakeCriticalSection](../atl/reference/ccomfakecriticalsection-class.md) odzwierciedla metod w `CComCriticalSection` bez podawania sekcję krytyczną. Metody w `CComFakeCriticalSection` nic nie rób.

- [CRTThreadTraits](../atl/reference/crtthreadtraits-class.md) udostępnia funkcję tworzenia wątku CRT. Jeśli wątek będzie używać funkcji CRT, należy użyć tej klasy.

- [Win32ThreadTraits](../atl/reference/win32threadtraits-class.md) udostępnia funkcję tworzenia wątku Windows. Jeśli wątek nie użyje funkcji CRT, należy użyć tej klasy.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../atl/atl-class-overview.md)

