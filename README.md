# THESIS-
import React from "react";

// TopNavBar Componet
const TopNavBar: React.FC = () => {
  return (
    <header className="top-navbar">
      <div className="navbar-brand">
        <span className="logo-name">Work Study Connect</span>
      </div>
      <div className="user-info">
        <div className="user-details">
          <span>Student</span>
        </div>
        <span className="notification-badge">ST</span>
      </div>
    </header>
  );
};

interface MenuItemProps {
  name: string;
}

const menuItems = [
  { name: "Work Study" },
  { name: "Selling Items" },
  { name: "Professor Research" },
  { name: "Internships" },
];

const MenuItem: React.FC<MenuItemProps> = ({ name }) => (
  <div className="p-4 rounded-lg cursor-pointer transition-colors duration-200 hover:bg-gray-100">
    <span>{name}</span>
  </div>
);

const SideBar: React.FC = () => {
  return (
    <div className="flex-none p-6 bg-white rounded-2xl shadow-lg">
      <h2 className="text-xl font-bold mb-4">Main Menu</h2>
      <div className="mb-6">
        <input
          className="w-full p-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
          type="text"
          placeholder="Menu Search"
        />
      </div>

      <nav className="flex flex-col gap-2">
        {menuItems.map((item, index) => (
          <MenuItem key={index} name={item.name} />
        ))}
      </nav>
    </div>
  );
};

interface WorkStudyCardProps {
  jobTitle: string;
  datePosted: string;
  requirements: string;
}

const WorkStudyCard: React.FC<WorkStudyCardProps> = ({
  jobTitle,
  datePosted,
  requirements,
}) => {
  return (
    <div className="p-6 bg-white rounded-2xl shadow-lg">
      <h3 className="text-lg font-semibold mb-2">{jobTitle}</h3>
      <p className="text-sm text-gray-500 mb-1">Date Posted: {datePosted}</p>
      <p className="text-sm text-gray-700 mb-4">Requirements: {requirements}</p>
      <button className="px-4 py-2 bg-blue-600 text-white rounded-lg hover:bg-blue-700 transition-colors">Apply Now</button>
    </div>
  );
};

function App() {
  return (
    <div className="flex flex-col min-h-screen bg-gray-50 p-8">
      <div className="mb-8">
        <TopNavBar />
      </div>
      <div className="flex-grow flex gap-8">
        <SideBar />
        <div className="flex-grow p-8 bg-gray-100 rounded-2xl shadow-lg flex flex-col items-center justify-center">
          <h2 className="text-2xl font-bold text-gray-800 mb-4">Work Study Opportunities</h2>
          <WorkStudyCard
            jobTitle="Test"
            datePosted="111"
            requirements="test"
          />
        </div>
      </div>
    </div>
  );
}

export default App;
