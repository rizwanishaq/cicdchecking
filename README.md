# Python CI/CD with GitHub Actions

This is a simple Python project with a CI/CD pipeline set up using GitHub Actions. The pipeline performs the following tasks:
- Runs unit tests using `pytest`.
- Installs dependencies directly from the `requirements.txt` file.

## Project Setup

1. **Clone the Repository**

    ```bash
    git clone https://github.com/rizwanishaq/python-github-actions.git
    cd python-github-actions
    ```

2. **Create and Activate Virtual Environment** *(Optional)*

    You can create and activate a virtual environment locally if you prefer:

    ```bash
    python -m venv venv
    source venv/bin/activate   # On Windows use venv\Scripts\activate
    ```

3. **Install Dependencies**

    You can install the dependencies using:

    ```bash
    pip install -r requirements.txt
    ```

    This will install all the required packages, including `pytest`.

4. **Run Tests Locally**

    To run the unit tests locally:

    ```bash
    pytest
    ```

## CI/CD with GitHub Actions

This project includes a GitHub Actions workflow to automate the CI process:

1. **Testing**

    - Every time you push code to the `main` branch or create a pull request, GitHub Actions will:
        - Install the required dependencies using `pip install -r requirements.txt`.
        - Run unit tests using `pytest`.

2. **Workflow File**

    The GitHub Actions workflow is defined in the `.github/workflows/ci.yml` file.

    ```yaml
    name: Python CI

    on:
      push:
        branches:
          - main
      pull_request:
        branches:
          - main

    jobs:
      test:
        runs-on: ubuntu-latest

        steps:
          - name: Checkout repository
            uses: actions/checkout@v4

          - name: Set up Python
            uses: actions/setup-python@v4
            with:
              python-version: "3.10"

          - name: Install dependencies
            run: |
              pip install -r requirements.txt  # Install dependencies directly from requirements.txt

          - name: Run tests
            run: pytest  # Run tests without virtual environment
    ```

    This workflow ensures that your tests are automatically run on every push or pull request to the `main` branch.

## Requirements

- Python 3.x
- `pytest` for testing

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

