# lab-04
```
name: formatter_apl
on:
  push:
    branches: 
      - main

jobs:
  Libraries:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2 
      - name: formatter_lib
        shell: bash
        run: |
          cd formatter_lib
          cmake -H. -B_build
          cmake --build _build
          
      - name: formatter_ex_lib
        shell: bash
        run: |
          mkdir _build
          cd _build
          cmake ..
          cmake --build .
          
      - name: solver_lib
        shell: bash
        run: |
          cd solver_lib
          cmake -H. -B_build
          cmake --build _build
  Build_Hello_World:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: build_hello_world
        shell: bash
        run: |
          mkdir hello_world
          cd hello_world
          cmake ..
          cmake --build .
          
      - name: hello_output
        shell: bash
        run: |
          cd hello_world/hello_world_application
          ./hello_world
          
  Build_Solver_App:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: build_solver
        shell: bash
        run: |
          mkdir solver
          cd solver
          cmake ..
          cmake --build .
          
      - name: output_solver
        shell: bash
        run: |
          cd solver/solver_application
          ./equation 1 2 -3
```
