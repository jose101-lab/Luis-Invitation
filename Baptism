import urllib.parse
import streamlit as st
from PIL import Image

st.set_page_config(
    page_title="Baptism Invitation",
    page_icon="🕊️",
    layout="centered"
)

# Custom Styling
st.markdown("""
    <style>
    .invitation-card {
        background-color: #fdfbf7;
        padding: 30px;
        border-radius: 15px;
        border: 2px solid #e0d7c6;
        box-shadow: 0px 4px 15px rgba(0,0,0,0.08);
        text-align: center;
        color: #4a4a4a;
        margin-top: 10px;
        margin-bottom: 20px;
    }
    .invitation-title { font-family: 'Georgia', serif; font-size: 28px; color: #8b7355; }
    .invitation-subtitle { font-family: 'Georgia', serif; font-style: italic; font-size: 16px; color: #7a7a7a; margin-bottom: 20px; }
    .invitation-name { font-family: 'Georgia', serif; font-size: 32px; font-weight: bold; color: #2c3e50; margin: 15px 0; }
    .invitation-details { font-size: 16px; line-height: 1.6; margin-top: 15px; }
    .invitation-footer { font-size: 14px; font-style: italic; margin-top: 25px; color: #666; }
    </style>
""", unsafe_allow_html=True)

# Read query parameters from URL if present
query_params = st.query_params

default_child = query_params.get("child", "Baby Alexander")
default_parents = query_params.get("parents", "John & Sarah Doe")
default_church = query_params.get("church", "St. Mary's Cathedral")
default_reception = query_params.get("reception", "Grand Ballroom, Hotel Royale")
default_godparents = query_params.get("godparents", "Michael Smith & Emily Davis")
default_rsvp = query_params.get("rsvp", "RSVP by Oct 1st: (555) 123-4567")

st.title("🕊️ Baptism Invitation")

# Sidebar Inputs
st.sidebar.header("📝 Invitation Details")

child_name = st.sidebar.text_input("Child's Name", value=default_child)
parents_names = st.sidebar.text_input("Parents' Names", value=default_parents)

date_input = st.sidebar.date_input("Date")
time_input = st.sidebar.time_input("Time")

church_venue = st.sidebar.text_input("Church / Ceremony Venue", value=default_church)
reception_venue = st.sidebar.text_input("Reception Venue (Optional)", value=default_reception)

godparents = st.sidebar.text_area("Godparents", value=default_godparents)
rsvp_info = st.sidebar.text_input("RSVP Contact Information", value=default_rsvp)

# Image Uploader
st.sidebar.header("🖼️ Upload Photo")
uploaded_file = st.sidebar.file_uploader("Upload JPEG/PNG Photo", type=["jpg", "jpeg", "png"])

# Card Output
st.markdown(f"""
<div class="invitation-card">
    <div style="font-size: 36px; margin-bottom: 10px;">🕊️</div>
    <div class="invitation-title">Holy Baptism</div>
    <div class="invitation-subtitle">You are cordially invited to celebrate the baptism of</div>
    <div class="invitation-name">{child_name}</div>
    <p><em>Child of {parents_names}</em></p>
""", unsafe_allow_html=True)

if uploaded_file is not None:
    image = Image.open(uploaded_file)
    col1, col2, col3 = st.columns([1, 2, 1])
    with col2:
        st.image(image, use_container_width=True)

st.markdown(f"""
    <hr style="border: 0; height: 1px; background: #e0d7c6; margin: 20px 0;">
    <div class="invitation-details">
        <p>📅 <strong>Date:</strong> {date_input.strftime('%B %d, %Y')}<br>
        ⏰ <strong>Time:</strong> {time_input.strftime('%I:%M %p')}</p>
        
        <p>⛪ <strong>Ceremony:</strong> {church_venue}</p>
        {"<p>🍽️ <strong>Reception:</strong> " + reception_venue + "</p>" if reception_venue else ""}
        {"<p>🙏 <strong>Godparents:</strong><br>" + godparents.replace('\n', '<br>') + "</p>" if godparents else ""}
    </div>
    
    <div class="invitation-footer">
        <p>{rsvp_info}</p>
    </div>
</div>
""", unsafe_allow_html=True)

# Generate Shareable Link Feature
st.subheader("🔗 Share via Messenger / Viber")

# Replace this base URL with your actual deployed Streamlit URL
base_url = "https://your-app-name.streamlit.app"  

params = {
    "child": child_name,
    "parents": parents_names,
    "church": church_venue,
    "reception": reception_venue,
    "godparents": godparents,
    "rsvp": rsvp_info
}

encoded_params = urllib.parse.urlencode(params)
shareable_url = f"{base_url}/?{encoded_params}"

st.code(shareable_url, language="text")
st.caption("Copy the link above and send it directly via Messenger or Viber!")
