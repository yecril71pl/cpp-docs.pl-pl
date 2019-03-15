---
title: DCOMCNFG
ms.date: 11/04/2016
helpviewer_keywords:
- DCOMCNFG utility
- DCOM, configuring in ATL
ms.assetid: 5a8126e9-ef27-40fb-a66e-9dce8d1a7e80
ms.openlocfilehash: a389a46cd02b40cef46d687743fd3416cc4f3154
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818583"
---
# <a name="dcomcnfg"></a>DCOMCNFG

DCOMCNFG to narzędzie Windows NT 4.0, które można skonfigurować różne ustawienia specyficzne dla modelu DCOM w rejestrze. W oknie DCOMCNFG ma trzy strony: Zabezpieczenia domyślne, właściwości domyślne i aplikacji. W obszarze Windows 2000 na czwartej stronie domyślne protokołów, jest obecny.

## <a name="default-security-page"></a>Domyślna strona zabezpieczeń

Aby określić domyślne uprawnienia dla obiektów w systemie, można użyć strony Zabezpieczenia domyślne. Strona domyślna zabezpieczeń będzie mieć trzy sekcje: Dostępu, uruchamiania i konfiguracji. Aby zmienić ustawienia domyślne sekcji, kliknij odpowiedni **Edytuj domyślne** przycisku. Te ustawienia domyślne zabezpieczeń są przechowywane w kluczu rejestru `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE`.

## <a name="default-protocols-page"></a>Domyślna strona protokołów

Ta strona wyświetla zestaw protokołów sieciowych, które są dostępne dla modelu DCOM na tej maszynie. Kolejność odzwierciedla priorytet, w którym będą używane; pierwszy na liście ma najwyższy priorytet. Protokoły, można dodać lub usunąć z tej strony.

## <a name="default-properties-page"></a>Strona właściwości domyślne

Na stronie właściwości domyślne należy wybrać **Włącz model obiektów rozproszonych COM na tym komputerze** pole wyboru, jeśli chcesz, aby klienci na innych komputerach, do obiektów COM dostępu uruchomionych na tej maszynie. Wybranie tej opcji ustawia `HKEY_LOCAL_MACHINE\Software\Microsoft\OLE\EnableDCOM` wartość `Y`.

## <a name="applications-page"></a>Strona aplikacji

Możesz zmienić ustawienia dla określonego obiektu ze strony aplikacji. Po prostu wybierz ją z listy i kliknij **właściwości** przycisku. W oknie właściwości zawiera pięć strony:

- Strona Ogólne potwierdza aplikację, którą pracujesz.

- Na stronie Lokalizacja pozwala określić, gdzie aplikacja powinna działać gdy klient wywołuje `CoCreateInstance` na odpowiedni identyfikator CLSID. Jeśli wybierzesz **Uruchom aplikację na następującym komputerze** pole wyboru, a następnie wprowadź nazwę komputera, a następnie `RemoteServerName` wartość jest dodawana w obszarze AppID dla tej aplikacji. Czyszczenie **Uruchom aplikację na tym komputerze** zmienia nazwę pola wyboru `LocalService` wartość `_LocalService` i dzięki temu wyłącza je.

- Strona zabezpieczeń jest podobna do strony Zabezpieczenia domyślne, w oknie DCOMCNFG, z tą różnicą, że te ustawienia dotyczą tylko w bieżącej aplikacji. Ponownie te ustawienia są przechowywane w obszarze identyfikator aplikacji dla tego obiektu.

- Na stronie Identyfikowanie identyfikuje użytkownika, który jest używany do uruchamiania aplikacji.

- Na stronie punkty końcowe, wyświetla zestaw protokołów i punktów końcowych dostępne do użycia przez klientów dla wybranego serwera modelu DCOM.

## <a name="see-also"></a>Zobacz także

[Usługi](../atl/atl-services.md)
