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
