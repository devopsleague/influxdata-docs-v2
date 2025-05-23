
Use [`fill()`](/flux/v0/stdlib/universe/fill/)
to replace _null_ values with:

- [the previous non-null value](#fill-with-the-previous-value)
- [a specified value](#fill-with-a-specified-value)

<!-- -->
```js
data
    |> fill(usePrevious: true)

// OR

data
    |> fill(value: 0.0)
```

{{% note %}}
#### Fill empty windows of time
The `fill()` function **does not** fill empty windows of time.
It only replaces _null_ values in existing data.
Filling empty windows of time requires time interpolation
_(see [influxdata/flux#2428](https://github.com/influxdata/flux/issues/2428))_.
{{% /note %}}

## Fill with the previous value
To fill _null_ values with the previous **non-null** value, set the `usePrevious` parameter to `true`.

{{% note %}}
Values remain _null_ if there is no previous non-null value in the table.
{{% /note %}}

```js
data
    |> fill(usePrevious: true)
```

{{< flex >}}
{{% flex-content %}}
**Given the following input:**

| _time                | _value |
|:-----                | ------:|
| 2020-01-01T00:01:00Z | null   |
| 2020-01-01T00:02:00Z | 0.8    |
| 2020-01-01T00:03:00Z | null   |
| 2020-01-01T00:04:00Z | null   |
| 2020-01-01T00:05:00Z | 1.4    |
{{% /flex-content %}}
{{% flex-content %}}
**`fill(usePrevious: true)` returns:**

| _time                | _value |
|:-----                | ------:|
| 2020-01-01T00:01:00Z | null   |
| 2020-01-01T00:02:00Z | 0.8    |
| 2020-01-01T00:03:00Z | 0.8    |
| 2020-01-01T00:04:00Z | 0.8    |
| 2020-01-01T00:05:00Z | 1.4    |
{{% /flex-content %}}
{{< /flex >}}

## Fill with a specified value
To fill _null_ values with a specified value, use the `value` parameter to specify the fill value.
_The fill value must match the [data type](/flux/v0/spec/types/#basic-types)
of the [column](/flux/v0/stdlib/universe/fill/#column)._

```js
data
    |> fill(value: 0.0)
```

{{< flex >}}
{{% flex-content %}}
**Given the following input:**

| _time                | _value |
|:-----                | ------:|
| 2020-01-01T00:01:00Z | null   |
| 2020-01-01T00:02:00Z | 0.8    |
| 2020-01-01T00:03:00Z | null   |
| 2020-01-01T00:04:00Z | null   |
| 2020-01-01T00:05:00Z | 1.4    |
{{% /flex-content %}}
{{% flex-content %}}
**`fill(value: 0.0)` returns:**

| _time                | _value |
|:-----                | ------:|
| 2020-01-01T00:01:00Z | 0.0    |
| 2020-01-01T00:02:00Z | 0.8    |
| 2020-01-01T00:03:00Z | 0.0    |
| 2020-01-01T00:04:00Z | 0.0    |
| 2020-01-01T00:05:00Z | 1.4    |
{{% /flex-content %}}
{{< /flex >}}
