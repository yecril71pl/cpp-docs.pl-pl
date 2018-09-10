---
title: Ograniczenia dotyczące nazwy symbolu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.name
dev_langs:
- C++
helpviewer_keywords:
- symbol names
- symbols [C++], names
- restrictions, symbol names
ms.assetid: 4ae7f695-ca86-4f4b-989a-fe6f89650ff7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 67527717319c4b571ff4b72b83d718c0ac149586
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313328"
---
# <a name="symbol-name-restrictions"></a>Ograniczenia dotyczące nazwy symbolu

Ograniczenia dotyczące nazwy symbolu są następujące:

- Wszystkie [symbole](../windows/symbols-resource-identifiers.md) musi być unikatowa w zakresie aplikacji. Zapobiega to sprzecznych definicji symbolu w plikach nagłówkowych.

- Nieprawidłowe znaki dla nazwy symbolu to A-Z, a – z, 0-9 i znaki podkreślenia (_).

- Nazwy symboli nie może zaczynać się liczbą i są ograniczone do 247 znaków.

- Nazwy symboli nie może zawierać spacji.

- Nazwy symboli nie jest uwzględniana wielkość liter, ale są zachowywane w przypadku pierwszej definicji symbolu. Plik nagłówka, który definiuje symbole jest używany przez kompilator/Edytor zasobów i C++ programy do odwoływania się zasoby zdefiniowane w pliku zasobów. Dwie nazwy symbolu które różnią się, tylko w przypadku, program w języku C++ zostanie wyświetlony dwa oddzielne symbole, gdy kompilator/Edytor zasobów zostanie wyświetlony obie nazwy jako odnoszące się do jednego pojedynczego symbolu.

   > [!NOTE]
   > Jeśli nie podlegają schemat nazwę standardowego symbolu (ID*_[keyword]) opisane poniżej, a Twoja nazwa symbolu stanie się być taka sama jak słowo kluczowe wiadomo, że kompilator skryptu zasobów, próba skompilowania pliku skryptu zasobu spowoduje błąd pozornie losowe Generowanie, który jest trudny do zdiagnozowania. Aby tego uniknąć, należy przestrzegać standardowych schemat nazewnictwa.

Nazwy symboli ma opisowe prefiksy, które wskazują rodzaj zasobu lub obiektów, które reprezentują. Prefiksy te opisowy zaczynają się od identyfikatora kombinację tekstu Biblioteka Microsoft Foundation Class (MFC) używa konwencji nazewnictwa symbol pokazano w poniższej tabeli.

|Kategoria|Prefiks|Zastosowanie|
|--------------|------------|---------|
|Resources|IDR_ IDD_ IDC_ IDI_ IDB_|Akcelerator lub menu (i skojarzone lub niestandardowe zasoby) okno dialogowe mapę bitową ikony kursora|
|Elementy menu|ID_|Element menu|
|Polecenia|ID_|Polecenie|
|Formanty i okien podrzędnych|IDC_|Formant|
|Ciągi|IDS_|Parametry w tabeli ciągów|
|MFC|AFX_|Zarezerwowane dla wstępnie zdefiniowane symbole MFC|

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Zmiana symbolu lub nazwy symbolu (ID)](../windows/changing-a-symbol-or-symbol-name-id.md)  
[Ograniczenia dotyczące wartości symbolu](../windows/symbol-value-restrictions.md)  
[Wstępnie zdefiniowane identyfikatory symboli](../windows/predefined-symbol-ids.md)