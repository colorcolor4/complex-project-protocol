# CC_Develope_Spec — <project name>

> Self-contained spec for Claude Code to implement directly. Fill every `<...>`.

## 1. Goal & Done-definition
- Goal: <≤3 bullets>
- Done when: <1-sentence success criterion + measurable checks>

## 2. Architecture (from S1)
- Chosen architecture: <name + 1-line why>
- Physics line: <real-world model in one paragraph>
- Software line: <what gets built in one paragraph>

## 3. Modules & Equations (from S2)
| Module | Responsibility | Equation IDs |
|--------|----------------|--------------|
| <m1>   | <...>          | (1),(2)      |

Equations:
- (1) <LaTeX>
- (2) <LaTeX>

Theory-vs-practice gaps / calibration knobs: <list>

## 4. Software Contract (from S3)
### File structure
```
<tree>
```
### Function signatures
```python
def <fn>(<args>) -> <ret>:  # implements (n); <one-line behavior>
```
### Data shapes
- <name>: <type / shape / units>

### Algorithm steps (bound to equation IDs)
1. <step> → (1)
2. <step> → (2)

### Dependencies
- <pkg==version>, <pkg>

## 5. Two-layer Validation
### Layer 1 — unit / analytic (per equation)
- test_<eq>: <input → expected, tolerance>

### Layer 2 — integration / physical plausibility (end-to-end)
- test_<flow>: <scenario → expected behavior / bound>
