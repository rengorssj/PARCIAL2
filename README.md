# PARCIAL 2 - Desarrollo de Software II

Calculadora con Integración Continua usando PHP, PHPUnit y GitHub Actions.

[![PHP CI](https://github.com/rengorssj/PARCIAL2/actions/workflows/php-ci.yml/badge.svg)](https://github.com/rengorssj/PARCIAL2/actions/workflows/php-ci.yml)

---

## URL del repositorio

https://github.com/rengorssj/PARCIAL2

---

## Integrantes

- Juan Diego Holguin Perez
- Alan Andres Silva Diaz

---

## Estructura del proyecto

```
PARCIAL2/
├── .github/
│   └── workflows/
│       └── php-ci.yml        # Pipeline de Integración Continua
├── src/
│   └── Calculadora.php       # Clase Calculadora (lógica de negocio)
├── tests/
│   └── CalculadoraTest.php   # Pruebas unitarias con PHPUnit
├── composer.json             # Dependencias y autoload
└── README.md                 # Documentación del proyecto
```

---

## Clase Calculadora (`src/Calculadora.php`)

Clase en el namespace `App` con cuatro operaciones básicas:

| Método | Descripción |
|---|---|
| `sumar($a, $b)` | Retorna la suma de `$a` y `$b` |
| `restar($a, $b)` | Retorna la resta de `$a` y `$b` |
| `multiplicar($a, $b)` | Retorna el producto de `$a` y `$b` |
| `dividir($a, $b)` | Retorna la división de `$a` entre `$b`. Si `$b` es 0, lanza `\InvalidArgumentException` |

---

## Pruebas unitarias (`tests/CalculadoraTest.php`)

Se implementaron 5 pruebas unitarias aplicando TDD:

| Prueba | Entrada | Resultado esperado | Estado |
|---|---|---|---|
| `testSuma()` | `sumar(2, 3)` | `5` | ✅ |
| `testResta()` | `restar(4, 3)` | `1` | ✅ |
| `testMultiplicacion()` | `multiplicar(4, 3)` | `12` | ✅ |
| `testDivision()` | `dividir(6, 3)` | `2` | ✅ |
| `testDivisionPorCeroLanzaExcepcion()` | `dividir(5, 0)` | `\InvalidArgumentException` | ✅ |

Para ejecutar las pruebas localmente:

### Requisitos

- PHP 8.0 o superior instalado
- Composer instalado globalmente
- Git

### Pasos

```bash
# 1. Clonar el repositorio
git clone https://github.com/rengorssj/PARCIAL2.git
cd PARCIAL2

# 2. Instalar dependencias (PHPUnit 10)
composer install

# 3. Ejecutar las pruebas unitarias
./vendor/bin/phpunit tests
```

### Salida esperada

```
PHPUnit 10.x.x by Sebastian Bergmann and contributors.

.....                                                               5 / 5 (100%)

Time: 00:00.xxx, Memory: xx.xx MB

OK (5 tests, 5 assertions)
```

---

## Pipeline de Integración Continua (GitHub Actions)

El workflow `php-ci.yml` se ejecuta automáticamente en cada push o PR a las ramas `main` y `desarrollo`:

1. **Descargar código** — `actions/checkout@v3`
2. **Configurar PHP 8.2** — `shivammathur/setup-php@v2` con extensiones mbstring y xml
3. **Instalar dependencias** — `composer install --no-progress --prefer-dist`
4. **Ejecutar pruebas** — `./vendor/bin/phpunit tests`

---

## Historial de ejecuciones (Actions)

| Run | Commit | Resultado |
|---|---|---|
| Run 1 | [`f837c41`](https://github.com/rengorssj/PARCIAL2/commit/f837c41) — Archivos base (3 pruebas iniciales) | ✅ Verde |
| Run 2 | [`37eb438`](https://github.com/rengorssj/PARCIAL2/commit/37eb438) — Agregada prueba de división | ❌ Rojo |
| Run 3 | [`595d499`](https://github.com/rengorssj/PARCIAL2/commit/595d499) — Implementada función dividir | ✅ Verde |
| Run 4 | [`344ba5e`](https://github.com/rengorssj/PARCIAL2/commit/344ba5e) — Agregada prueba de división por cero | ❌ Rojo |
| Run 5 | [`d08d275`](https://github.com/rengorssj/PARCIAL2/commit/d08d275) — Manejada división por cero con excepción | ✅ Verde |
| Run 6 | [`e5392fd`](https://github.com/rengorssj/PARCIAL2/commit/e5392fd) — README con badge y URL | ✅ Verde |
| Run 7 | [`4f7eb42`](https://github.com/rengorssj/PARCIAL2/commit/4f7eb42) — Nombres de los integrantes | ✅ Verde |
| Run 8 | [`bd8d941`](https://github.com/rengorssj/PARCIAL2/commit/bd8d941) — README mejorado con estructura y detalle | ✅ Verde |

El flujo rojo → verde demuestra la aplicación correcta de TDD e Integración Continua.
