---
title: Klasa CCriticalSection | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
dev_langs:
- C++
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e5147faaf0170a10295006f12d7e95f5dfd3e8d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380701"
---
# <a name="ccriticalsection-class"></a>Klasa CCriticalSection

Przedstawia "sekcję krytyczną" — obiektem synchronizacji umożliwiającym jednemu wątkowi w czasie uzyskać dostęp do zasobów lub sekcji kodu.

## <a name="syntax"></a>Składnia

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Konstruuje `CCriticalSection` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSection::Lock](#lock)|Umożliwia dostęp do `CCriticalSection` obiektu.|
|[CCriticalSection::Unlock](#unlock)|Wersje `CCriticalSection` obiektu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION *](#operator_critical_section_star)|Pobiera wskaźnik do obiektu CRITICAL_SECTION wewnętrznego.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Obiekt CRITICAL_SECTION.|

## <a name="remarks"></a>Uwagi

Sekcje krytyczne są przydatne, gdy tylko jeden wątek jednocześnie można zezwolić na modyfikowanie danych lub innego zasobu kontrolowany. Na przykład dodawanie węzłów do połączonej listy jest procesem, który powinien być dozwolony tylko przez jeden wątek jednocześnie. Za pomocą `CCriticalSection` obiektu do kontrolowania liście połączonej, tylko jeden wątek jednocześnie uzyskać dostęp do listy.

> [!NOTE]
>  Funkcje `CCriticalSection` klasy są dostarczane przez faktyczny obiekt Win32 CRITICAL_SECTION.

Sekcje krytyczne są używane zamiast muteksy (zobacz [CMutex](../../mfc/reference/cmutex-class.md)) kiedy szybkość ma krytyczne znaczenie i zasobu nie będą używane przez granice procesu.

Istnieją dwie metody przy użyciu `CCriticalSection` obiektu: autonomiczne i osadzone w klasie.

- Autonomiczny metodę, aby używać autonomicznego `CCriticalSection` obiektów, konstruowania `CCriticalSection` obiektu, kiedy jest to konieczne. Po pomyślnym zwrotu z konstruktora, jawnie zablokować dostęp do obiektu z wywołaniem [blokady](#lock). Wywołaj [Unlock](#unlock) po zakończeniu uzyskiwania dostępu do sekcji krytycznych. Ta metoda, podczas przejrzyste komuś czytanie kodu źródłowego, jest bardziej podatne na błędy, ponieważ należy pamiętać zablokować i odblokować sekcję krytyczną, przed i po nim dostępu.

     Bardziej preferowaną metodą jest użycie [CSingleLock](../../mfc/reference/csinglelock-class.md) klasy. Ma on także `Lock` i `Unlock` metody, ale nie musi się martwić o odblokowanie zasobu, jeśli wystąpi wyjątek.

- Osadzona metoda klasy można także udostępnić w wielu wątkach, dodając `CCriticalSection`— element członkowski danych typu klasy i blokowanie składowej danych, które w razie.

Aby uzyskać więcej informacji na temat korzystania z `CCriticalSection` obiektów, zobacz artykuł [wielowątkowość: jak używać klas synchronizacji](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxmt.h

##  <a name="ccriticalsection"></a>  CCriticalSection::CCriticalSection

Konstruuje `CCriticalSection` obiektu.

```
CCriticalSection();
```

### <a name="remarks"></a>Uwagi

Dostęp i zwalniania `CCriticalSection` obiektu, Utwórz [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu, a następnie wywołać jej [blokady](../../mfc/reference/csinglelock-class.md#lock) i [Unlock](../../mfc/reference/csinglelock-class.md#unlock) funkcji elementów członkowskich. Jeśli `CCriticalSection` obiekt jest używany autonomiczny, wywoływanie jej [Unlock](#unlock) funkcja elementu członkowskiego do jego zwolnienia.

Jeśli Konstruktor nie powiedzie się można przydzielić pamięci wymagany system, wyjątek pamięci (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) jest automatycznie generowany.

### <a name="example"></a>Przykład

  Zobacz przykład [CCriticalSection::Lock](#lock).

##  <a name="lock"></a>  CCriticalSection::Lock

Wywołanie tej funkcji elementu członkowskiego w celu uzyskania dostępu do obiektu sekcję krytyczną.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parametry

*dwTimeout*<br/>
`Lock` ignoruje wartości tego parametru.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

`Lock` to wywołanie blokujące, które nie zwracają do momentu zasygnalizowania obiektu sekcję krytyczną (staje się dostępny).

Jeśli konieczne są Przekroczono limit czasu oczekiwania, możesz użyć [CMutex](../../mfc/reference/cmutex-class.md) zamiast obiektu `CCriticalSection` obiektu.

Jeśli `Lock` nie może przydzielić pamięci systemu to konieczne, wyjątek pamięci (typu [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) jest automatycznie generowany.

### <a name="example"></a>Przykład

W tym przykładzie przedstawiono podejście zagnieżdżonych sekcję krytyczną poprzez kontrolowanie dostępu do udostępnionego zasobu (statyczne `_strShared` obiektów) przy użyciu udostępnionego `CCriticalSection` obiektu. `SomeMethod` Funkcji pokazuje aktualizowanie zasobu udostępnionego w bezpieczny sposób.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

##  <a name="m_sect"></a>  CCriticalSection::m_sect

Zawiera obiekt sekcję krytyczną, który jest używany przez wszystkie `CCriticalSection` metody.

```
CRITICAL_SECTION m_sect;
```

##  <a name="operator_critical_section_star"></a>  CCriticalSection::operator CRITICAL_SECTION *

Pobiera obiekt CRITICAL_SECTION.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby pobrać wskaźnika do obiektu wewnętrznego CRITICAL_SECTION.

##  <a name="unlock"></a>  CCriticalSection::Unlock

Wersje `CCriticalSection` obiekt do użycia przez inny wątek.

```
BOOL Unlock();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wartość różną od zera `CCriticalSection` wątek został właścicielem obiektu i wersji zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Jeśli `CCriticalSection` jest używana autonomiczna, `Unlock` musi zostać wywołana natychmiast po zakończeniu korzystania z zasobów w wartości clientauthtrustmode sekcję krytyczną. Jeśli [CSingleLock](../../mfc/reference/csinglelock-class.md) obiektu jest używana, `CCriticalSection::Unlock` zostanie wywołana przez obiekt blokady `Unlock` funkcja elementu członkowskiego.

### <a name="example"></a>Przykład

  Zobacz przykład [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Zobacz też

[Klasa CSyncObject](../../mfc/reference/csyncobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMutex](../../mfc/reference/cmutex-class.md)
