import urllib.request
import py3Dmol

# Select a protein using its PDB ID
pdb_id = "1CRN"

# Download protein structure data
url = f"https://files.rcsb.org/download/{pdb_id}.pdb"

try:
    with urllib.request.urlopen(url) as response:
        pdb_data = response.read().decode("utf-8")

    # Create 3D protein visualization
    view = py3Dmol.view(width=800, height=600)
    view.addModel(pdb_data, "pdb")

    # Display protein as cartoon
    view.setStyle({"cartoon": {"color": "spectrum"}})

    # Set background
    view.setBackgroundColor("white")

    # Adjust camera
    view.zoomTo()

    # Save visualization as HTML
    view.write_html("protein_structure.html")

    print("Protein structure downloaded successfully!")
    print("Visualization saved as protein_structure.html")

except Exception as error:
    print("Error:", error)
    html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Protein Structure Visualization</title>

    <script src="https://3dmol.org/build/3Dmol-min.js"></script>

    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background: #eef6ff;
            margin: 0;
            padding: 20px;
        }

        h1 {
            color: #173b68;
        }

        p {
            color: #333;
        }

        #viewer {
            width: 100%;
            max-width: 800px;
            height: 450px;
            margin: 20px auto;
            position: relative;
            background: white;
            border: 2px solid #173b68;
            border-radius: 10px;
        }

        button {
            padding: 12px 20px;
            margin: 5px;
            background: #173b68;
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
        }

        button:hover {
            background: #2867a8;
        }

        footer {
            margin-top: 20px;
            color: #555;
        }
    </style>
</hea

